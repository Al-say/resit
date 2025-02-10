# MCP扩展使用指南

MCP (Model Context Protocol) 是一个允许扩展功能的协议系统。以下是添加MCP扩展的详细步骤：

## 1. 准备工作

- 确保Node.js已安装在系统上
- MCP服务器默认目录: `E:\Document\Cline\MCP`

## 2. 创建新的MCP服务器

使用以下命令创建新的MCP服务器：

```bash
cd E:\Document\Cline\MCP
npx @modelcontextprotocol/create-server 你的服务器名称
```

## 3. 配置MCP服务器

1. 进入创建的服务器目录
2. 安装所需依赖：`npm install`
3. 修改 `package.json` 确保包含：
```json
{
  "type": "module",
  "scripts": {
    "build": "tsc && node -e \"require('fs').chmodSync('build/index.js', '755')\""
  }
}
```
4. 根据需求编辑 `src/index.ts` 文件，实现所需功能

## 4. 添加到MCP配置

编辑MCP配置文件，位于：
`C:\Users\Alsay\AppData\Roaming\Code\User\globalStorage\saoudrizwan.claude-dev\settings\cline_mcp_settings.json`

添加新服务器配置：

```json
{
  "mcpServers": {
    "你的服务器名称": {
      "command": "node",
      "args": ["服务器构建文件路径"],
      "env": {
        "需要的环境变量": "对应的值"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

## 示例：创建天气API服务器

这是一个使用OpenWeather API的示例MCP服务器：

1. 创建服务器：
```bash
cd E:\Document\Cline\MCP
npx @modelcontextprotocol/create-server weather-server
cd weather-server
npm install axios
```

2. 编辑 `src/index.ts`：

```typescript
#!/usr/bin/env node
import { Server } from '@modelcontextprotocol/sdk/server/index.js';
import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js';
import {
  CallToolRequestSchema,
  ErrorCode,
  ListToolsRequestSchema,
  McpError,
} from '@modelcontextprotocol/sdk/types.js';
import axios from 'axios';

const API_KEY = process.env.OPENWEATHER_API_KEY;
if (!API_KEY) {
  throw new Error('OPENWEATHER_API_KEY environment variable is required');
}

class WeatherServer {
  private server: Server;
  private axiosInstance;

  constructor() {
    this.server = new Server(
      {
        name: 'weather-server',
        version: '0.1.0',
      },
      {
        capabilities: {
          tools: {},
        },
      }
    );

    this.axiosInstance = axios.create({
      baseURL: 'http://api.openweathermap.org/data/2.5',
      params: {
        appid: API_KEY,
        units: 'metric',
      },
    });

    this.setupToolHandlers();
    
    this.server.onerror = (error) => console.error('[MCP Error]', error);
    process.on('SIGINT', async () => {
      await this.server.close();
      process.exit(0);
    });
  }

  private setupToolHandlers() {
    this.server.setRequestHandler(ListToolsRequestSchema, async () => ({
      tools: [
        {
          name: 'get_weather',
          description: '获取指定城市的天气信息',
          inputSchema: {
            type: 'object',
            properties: {
              city: {
                type: 'string',
                description: '城市名称',
              },
            },
            required: ['city'],
          },
        },
      ],
    }));

    this.server.setRequestHandler(CallToolRequestSchema, async (request) => {
      if (request.params.name !== 'get_weather') {
        throw new McpError(
          ErrorCode.MethodNotFound,
          `未知工具: ${request.params.name}`
        );
      }

      const args = request.params.arguments;
      if (typeof args !== 'object' || !args || typeof args.city !== 'string') {
        throw new McpError(
          ErrorCode.InvalidParams,
          '无效的参数'
        );
      }

      try {
        const response = await this.axiosInstance.get('weather', {
          params: { q: args.city },
        });

        return {
          content: [
            {
              type: 'text',
              text: JSON.stringify({
                temperature: response.data.main.temp,
                conditions: response.data.weather[0].description,
                humidity: response.data.main.humidity,
                wind_speed: response.data.wind.speed,
              }, null, 2),
            },
          ],
        };
      } catch (error) {
        if (axios.isAxiosError(error)) {
          return {
            content: [
              {
                type: 'text',
                text: `Weather API error: ${
                  error.response?.data.message ?? error.message
                }`,
              },
            ],
            isError: true,
          };
        }
        throw error;
      }
    });
  }

  async run() {
    const transport = new StdioServerTransport();
    await this.server.connect(transport);
    console.error('Weather MCP server running on stdio');
  }
}

const server = new WeatherServer();
server.run().catch(console.error);
```

3. 构建服务器：
```bash
npm run build
```

4. 获取 OpenWeather API密钥：
- 访问 https://openweathermap.org/
- 注册账号并登录
- 在API keys部分获取密钥

5. 添加到MCP配置：
```json
{
  "mcpServers": {
    "weather": {
      "command": "node",
      "args": ["E:/Document/Cline/MCP/weather-server/build/index.js"],
      "env": {
        "OPENWEATHER_API_KEY": "你的API密钥"
      },
      "disabled": false,
      "autoApprove": []
    }
  }
}
```

## 使用说明

1. 服务器添加完成后，Claude会自动检测并列出可用的工具
2. 可以通过以下方式使用天气工具：
   - "查询北京的天气"
   - "上海现在天气如何？"
   - 等自然语言查询

## 注意事项

1. 确保服务器代码没有语法错误
2. 正确配置所有必需的环境变量
3. 构建路径在配置文件中必须使用正确的格式
4. 新添加的服务器需要重启VSCode才能生效

这个指南提供了基本的MCP扩展创建和配置流程。你可以基于这个模板开发更多功能，如翻译服务、AI绘画、文档处理等。每个服务器都可以实现自己的特定功能，扩展Claude的能力。

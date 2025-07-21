## 简介
本SDK为Python语言的开发者提供网盘MCP Server工具集的MCP Client调用示例，可以为您作为客户端调用网盘MCP Server提供参考。

## 使用准备
使用前需要先完成接入鉴权，鉴权流程参考【[使用准备](https://pan.baidu.com/union/doc/Wm9sl0i0j)】获取到您的Access Token。

## Client-Demo

## 1. 使用大模型
无论使用`Stdio`模式还是`SSE`模式，Demo默认使用千帆平台提供的`DeepSeek V3`模型来进行工具选择和结果处理。您也可以自行选择平台或模型，下面以千帆平台为例介绍运行流程。
### 1.1 获取千帆平台的API_KEY
点击【[千帆平台认证鉴权](https://cloud.baidu.com/doc/qianfan-api/s/ym9chdsy5)】获取千帆平台API_KEY。

### 1.2 将API_KEY设置到环境变量
您可以选用以下任一方式将API_KEY设置到环境变量中：
```
(1) 通过export命令
    export LLM_API_KEY=<您的API_KEY>
(2) 通过命令行运行
    Stdio模式：LLM_API_KEY=<您的API_KEY> uv run client_demo_stdio.py
    SSE模式：LLM_API_KEY=<您的API_KEY> uv run client_demo_sse.py
```
## 2. Stdio模式
> Demo文件：client_demo_stdio.py

### 2.1 创建配置文件
Demo中默认使用同目录的servers_config.json配置文件。在Stdio模式下，配置文件内容如下：
```
{
    "mcpServers": {
      "netdisk-stdio": {
        "command": "uv",
        "args": [
          "run",
          "--with",
          "mcp[cli]",
          "mcp",
          "run",
          "<您的MCP Server文件>"   // 例如：./netdisk.py
        ],
        "env": {
          "BAIDU_NETDISK_ACCESS_TOKEN": "<您的AccessToken>"
        }
      }
    }
}
```
### 2.2 运行方式
```
uv run client_demo_stdio.py
```
## 3. SSE模式
> Demo文件：client_demo_sse.py

### 3.1 创建配置文件
Demo程序默认使用同目录的servers_config.json配置文件。在SSE模式下，配置文件内容如下：
```
{
  "mcpServers": {
    "netdisk-sse": {
      "url": "https://mcp-pan.baidu.com/sse?access_token=<您的AccessToken>"
    }
  }
}
```

### 3.2 运行方式
```
uv run client_demo_sse.py
```

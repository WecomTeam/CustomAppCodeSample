本项目旨在用一个最小应用的形式，帮助开发者了解企业微信服务商代开发的基本流程和概念。

## 功能介绍

本项目基于 `Express` 与 `VueCli` 构建，主要用于向开发演示企业微信自建应用的常见开发场景，主要功能包括：

### 代开发模板回调

支持验证和接收来自企业微信的代开发模板回调请求，并给出相应的响应，支持回调类型：
- Get 方式，验证代开发模板回调 URL
- Post 方式，接收 `suite_ticket`
- Post 方式，新增企业授权 `create_auth` 
- Post 方式，重新获取应用 Secret `reset_permanent_code` 

### 基本信息看板

查看当前代开发应用模板的基本配置信息，包含 模板ID、模板Secret、Token、EncodingAESKey 等基本信息。

<img src="https://wwcdn.weixin.qq.com/node/wework/images/202211222049.e7f5db2d5f.png" width="640"  max-width="640" />


### 企业授权信息

查看当前代开发应用模板已经授权过的客户企业信息列表，包含企业的 CorpID、Secret、AgentID 等基本信息。

<img src="https://wwcdn.weixin.qq.com/node/wework/images/202211222050.178202f425.png" width="640"  max-width="640" />

## 项目说明

### 一、目录说明

```bash
/configs
    - suite_config.js.sample # 代开发配置信息 demo
/libs
    - tokens.js              # 代开发获取、读取 suite_ticket 等信息的方法
/routes
    - callback.js            # 用于接收和处理企业微信回调的路由逻辑
    - index.js               # 用于展示代开发基本信息的路由逻辑
/scratch                     # 用于临时缓存 suite_ticket 等数据
```

### 二、配置说明

`/configs/suite_config.js` 包含了完整的项目配置数据，针对不同的功能需要不同的权限，在使用对用的功能前请先确认对应的权限信息。

## 使用示例代码

### 一、下载代码示例

打开命令行工具，执行以下命令，下载服务端代码。

```bash
git clone https://github.com/WecomTeam/CustomAppCodeSample.git
```

### 二、配置项目信息

打开下载的代码工程，在 `/configs` 目录将 `suite_config.js.sample` 复制一份到 `suite_config.js` 文件，并根据实际项目情况补充以下配置信息：

**提示：** 该文件配置的信息极其重要，切勿泄漏。

```javascript
{
    // 模板信息 - 基本信息 中复制以下参数
    SuiteID : '',
    SuiteSecret: '',
    
    // 模板信息 - 回调配置 中复制以下参数
    Token: "",
    EncodingAESKey: "",

    // 代开发模板回调 URL 的path
    CallBackPath:'/command'
}
```

### 三、安装项目依赖

在已下载的示例代码项目根目录下，执行以下代码完成依赖安装：
```bash
# npm
npm install 
# yarn
yarn 
```

### 四、启动服务

执行以下命令，启动后端服务

```bash
# npm
npm run start
# yarn
yarn start
```

### 五、使用服务

#### 回调路由
根据在 `config/suite_config.js` 中 `CallBackPath` 的设置，当前代开发应用模板的回调URL为: 

```
http://localhost:8080/callback/command
```

关于设置企业微信代开发应用模板的回调，请参考官方教程 [如何接收企业微信代开发回调](https://developer.work.weixin.qq.com/tutorial/detail/64)。


#### 本地访问
在浏览器中访问 http://localhost:8080 检查服务是否启动成功。

## 更多教程
关于企业微信企业自建应用开发相关的内容，请参考企业微信官方教程 [服务商代开发应用](https://developer.work.weixin.qq.com/tutorial/detail/62)，关于企业微信开发更多的教程和指引，请查看 [官方开发教程](https://developer.work.weixin.qq.com/tutorial/)。


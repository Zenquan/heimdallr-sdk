# `@heimdallr-sdk/node`

> NodeJs监控基座，内置错误捕获sdk

可捕获错误类型

- 未捕获的错误

默认使用 get 上报，允许自定义请求函数

## Options

|配置名称|类型|描述|可选值|默认值|
|-|-|-|-|-|
|dsn|Object|上报接口配置信息|DSN|-|
|app|Object|应用信息|APPInfo|-|
|enabled|Boolean|是否向后台发送事件|true/false|true|
|plugins|Array|插件集合|-|-|
|debug|Boolean|控制台是否显示报错|true/false|true|
|sendFunc|Function|请求函数|-|-|

### DSN

|名称|类型|描述|可选值|
|-|-|-|-|
|host|String|上报接口域名地址|-|
|init|String|应用初始化接口地址|-|
|upload|String|信息上报接口地址|-|

### APPInfo

|名称|类型|描述|可选值|
|-|-|-|-|
|name|String|应用名称|-|
|leader|String|负责人|-|
|desc|String|应用描述|-|

### sendFunc

|参数|类型|描述|
|url|string|请求地址|
|params|Object|上报参数|

<font color=red>返回一个 Promise 实例</font>

for example:

```js
const heimdallerOptions = {
    dsn: {
            host: 'localhost:8888',
            init: '/project/init',
            upload: '/log/upload'
        },
        app: {
            name: 'playgroundAPP',
            leader: 'test',
            desc: 'test proj'
        },
        sendFunc: (url, params) => {
            return new Promise((rs, rj) => {
                // do something
                rs({
                    code: 0,
                    msg: 'success',
                    data: 'hello world'
                });
            })
        }
}
```

## Usage

```js
import heimdallr from "@heimdallr-sdk/node";
heimdallr({
    dsn: {
        host: 'localhost:8888',
        init: '/project/init',
        upload: '/log/upload'
    },
    app: {
        name: 'playgroundAPP',
        leader: 'test',
        desc: 'test proj'
    }
});
```
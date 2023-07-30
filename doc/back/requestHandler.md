## requestAdaptor


crud-edit.json 和 crud-new.json 所使用的适配器
```javascript

let jsonObj = {};

let content = JSON.parse(api.data.msgContent).content
let url = JSON.parse(api.data.msgContent).url
let title = JSON.parse(api.data.msgContent).title
let sendType = JSON.parse(api.data.msgContent).sendType
let picUrl = JSON.parse(api.data.msgContent).picUrl


// push通知栏
if(api.data.sendChannel == '20'){
    jsonObj.content = content
    jsonObj.url = url
    jsonObj.title = title
}
// 短信
if(api.data.sendChannel == '30'){
    jsonObj.url = url
    jsonObj.content = content
}
// 邮件
if(api.data.sendChannel == '40'){
    jsonObj.content = content
    jsonObj.title = title
}
// 企业微信
if (api.data.sendChannel == '70') {
    // 文本类型
    if (sendType == '10') {
        jsonObj.content = content
        jsonObj.sendType = sendType
    }
}
// 钉钉机器人
if (api.data.sendChannel == '80') {
    // 文本类型(text)
    if (sendType == '10') {
        jsonObj.content = content
        jsonObj.sendType = sendType
    }
    // 图文类型(FeedCard)
    if (sendType == '40') {
        jsonObj.sendType = sendType
        jsonObj.feedCards = JSON.stringify(api.data.feedCards)
    }
    // markdown类型(markdown)
    if (sendType == '80') {
        jsonObj.content = content
        jsonObj.sendType = sendType
        jsonObj.title = title
    }
    // 链接类型(link)
    if (sendType == '110') {
        jsonObj.content = content
        jsonObj.sendType = sendType
        jsonObj.title = title
        jsonObj.picUrl = picUrl
        jsonObj.url = url
    }
    // 卡片跳转(actionCard)
    if (sendType == '120') {
        jsonObj.title = title
        jsonObj.content = content
        jsonObj.btnOrientation = api.data.btnOrientation
        jsonObj.btns = JSON.stringify(api.data.btns)
        jsonObj.sendType = sendType
    }
}
// 钉钉工作消息
if (api.data.sendChannel == '90') {
    // 文本类型
    if (sendType == '10') {
        jsonObj.content = content
        jsonObj.sendType = sendType
    }
    // 语音类型
    if (sendType == '20') {
        jsonObj.sendType = sendType
        jsonObj.duration = api.data.duration
        jsonObj.mediaId = api.data.mediaId
    }
    // 文件类型 || 图片类型
    if (sendType == '60' || sendType == '100') {
        jsonObj.sendType = sendType
        jsonObj.mediaId = api.data.mediaId
    }
    // 链接类型
    if (sendType == '110') {
        jsonObj.content = content
        jsonObj.sendType = sendType
        jsonObj.title = title
        jsonObj.mediaId = api.data.mediaId
        jsonObj.url = url
    }
    // markdown类型(markdown)
    if (sendType == '80') {
        jsonObj.content = content
        jsonObj.sendType = sendType
        jsonObj.title = title
    }
    // 卡片跳转(actionCard)
    if (sendType == '120') {
        jsonObj.title = title
        jsonObj.content = content
        jsonObj.btnOrientation = api.data.btnOrientation
        jsonObj.btns = JSON.stringify(api.data.btns)
        jsonObj.sendType = sendType
    }
    
    // OA(actionCard)
    if (sendType == '130') {
        
        // 头部
        var head = {}
        head.bgcolor = api.data.dingDingOaHeadBgColor
        head.text = api.data.dingDingOaHeadTitle
        jsonObj.dingDingOaHead = head
        
        // body
        var body = {}
        body.title = api.data.dingDingOaTitle
        body.content = api.data.dingDingOaContent
        body.image = api.data.mediaId
        body.author = api.data.dingDingOaAuthor
        jsonObj.dingDingOaBody = body
        
        // 通用
        jsonObj.sendType = sendType
        jsonObj.url = url
    }
}

// 飞书群机器人
if (api.data.sendChannel == '110') {
    // 文本类型
    if (sendType == '10') {
        jsonObj.content = content
        jsonObj.sendType = sendType
    }

    // 通用
    jsonObj.sendType = sendType
    jsonObj.url = url
}

api.data.msgContent = JSON.stringify(jsonObj)
return api;

```


crud-list.json 所使用的适配器

```javascript

let jsonObj = {};

let content = JSON.parse(api.data.msgContent).content
let url = JSON.parse(api.data.msgContent).url
let title = JSON.parse(api.data.msgContent).title
let sendType = JSON.parse(api.data.msgContent).sendType
let picUrl = JSON.parse(api.data.msgContent).picUrl


// 钉钉机器人
if (api.data.sendChannel == '80') {
    // 图文类型(FeedCard)
    if (sendType == '40') {
        jsonObj.feedCards = JSON.stringify(api.data.feedCards)
        api.data.msgContent = JSON.stringify(jsonObj)
    }
}



return api;


```


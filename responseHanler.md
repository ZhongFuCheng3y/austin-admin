```js


// 调用接口前判断是否已登录
var openId = localStorage.getItem("openId");
if (openId != null && openId != 'null' && openId != '' && openId !== undefined) {
    alert("已登录，你的ID是：" + openId);
    window.location.href = 'index.html';
    return api;
}


// 轮询登录校验返回
if (payload.data != 'NO_LOGIN' && payload.status == '0') {
    localStorage.setItem("openId", payload.data.openId);
    alert("扫码已登录成功，你的ID是：" + payload.data.openId);
    window.location.href = 'index.html';
}
return payload;

```
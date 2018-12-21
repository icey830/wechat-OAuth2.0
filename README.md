wechat-OAuth2.0
===============

wechat oath2.0 Demo, 对应微信公众号开发者文档/用户管理/网页授权获取用户基本信息 

并且解决微信OAuth2.0网页授权只能设置一个回调域名的问题

## 使用方法

1. 部署`get-weixin-code.html`至你的微信授权回调域名的目录下

2. 使用方式类似于直接通过微信回调的方式，只是将回调地址改成了`get-weixin-code.html`所在的地址，另外省去了`response_type`参数（因为它只能为`code`）以及`#wechat_redirect`（它是固定的），它们会在`get-weixin-code.html`里面自己加上

3. `get-weixin-code.html`页面从微信那里拿到code之后会重新跳转回`redirect_uri`里面填写的url，并且在url后面带上`code`和`state`

## 详细示例

1. 前往微信公众平台->接口权限->网页授权获取用户基本信息->修改，填写授权回调页面域名，例如`www.abc.com`

2. 在`www.abc.com`域名下部署`get-weixin-code.html`，不一定是根目录，例如：`http://www.abc.com/xxx/get-weixin-code.html`

3. 假设你的`http://www.xyz.com/hello-world.html`这个页面需要获取微信授权，那么你应该使用以下地址来获取授权：`http://www.abc.com/xxx/get-weixin-code.html?appid=XXXX&scope=snsapi_base&state=testopenid&redirect_uri=http://www.xyz.com/testopenid.php`

4. 这样最终就会跳转到这样一个地址：`http://www.xyz.com/hello-world.html?code=XXXXXXXXXXXXXXXXX&state=testopenid`，从而你就拿到了授权`code`以及自定义的`state`参数了

## AccessToken
1. 基本信息
    - `access_token`是公众号的全局唯一接口调用凭据，公众号调用各接口时都需使用`access_token`
    - `access_token`的存储至少要保留512个字符空间
    - `access_token`的有效期目前为2个小时，需定时刷新，重复获取将导致上次获取的`access_token`失效
    - 可以网页获取, 也可以接口获取

2. 使用
    - 建议使用中控服务器统一获取和刷新`Access_token`
        - 其他业务逻辑服务器所使用的`access_token`均来自于该中控服务器，不应该各自去刷新
        - 否则容易造成冲突，导致`access_token`覆盖而影响业务
    - 目前`Access_token`的有效期通过返回的`expire_in`来传达
        - 目前是 7200 秒之内的值。
        - 中控服务器需要根据这个有效时间提前去刷新新`access_token`。
        - 在刷新过程中，中控服务器可对外继续输出的老`access_token`，此时公众平台后台会保证在5分钟内，新老`access_token`都可用，这保证了第三方业务的平滑过渡
    - `Access_token`的有效时间可能会在未来有调整
        - 所以中控服务器不仅需要内部定时主动刷新，还需要提供被动刷新`access_token`的接口
        - 这样便于业务服务器在API调用获知`access_token`已超时的情况下，可以触发`access_token`的刷新流程

3. 生成方式
    - 公众号可以使用AppID和AppSecret调用本接口来获取access_token
    - AppID和AppSecret可在“微信公众平台-开发-基本配置”页中获得
    - 调用接口时，请登录“微信公众平台-开发-基本配置”提前将服务器IP地址添加到IP白名单中，否则将无法调用成功。
    - 接口
        ```js
            // https请求方式: GET 
            https://api.weixin.qq.com/cgi-bin/token?grant_type=client_credential&appid=APPID&secret=APPSECRET

            // 参数说明
            grant_type	获取access_token填写client_credential
            appid	第三方用户唯一凭证
            secret	第三方用户唯一凭证密钥，即appsecret

            // 返回说明
            {"access_token":"ACCESS_TOKEN","expires_in":7200}
            access_token	获取到的凭证
            expires_in	    凭证有效时间，单位：秒
        ```


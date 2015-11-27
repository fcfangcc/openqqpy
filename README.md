openqqpy
========

OpenQQ SDK for Python

OpenQQ登录的python sdk.
 demo地址 http://www.xulu.cc/

github地址:https://github.com/xuluxu/openqqpy


目前支持功能

1. 获取授权登录地址,需要自己跳转.

2.获取access_token,设置access_token

3.获取openid,设置openid

4.执行api调用.返回结果为dict对象.

 

使用步骤:

1.获取登录链接

client = OpenQQClient(client_id='your client_id',client_secret='your client_secret',redirect_uri='登录成功后的回调地址',scope='需要使用的api')

client.get_auth_url()

2.授权成功后,会跳转至回调地址,并带有code参数.

这时可以通过code获得access_token

 client = OpenQQClient(client_id='your client_id',client_secret='your client_secret',redirect_uri='登录成功后的回调地址',scope='需要使用的api')

client.request_access_token(code) #返回access_token,expires_in

client.set_access_token( access_token,expires_in )

3.接第2步,获得openid

client.request_openid() #返回openid

client.set_openid(openid)

4.执行api调用,默认执行get请求,只需传入api地址,如果要使用POST需传入method和params

client.request_api('user/get_user_info')

 

时间有限描述比较仓促,后续会整理好readme...

## fangc20151126更新信息:

获取Authorization Code函数里面添加了state参数，现要求必须添加该参数

移除了获取Access Token里面的state参数，现在已不需要该参数

_encode_params现用urllib.urlencode替代
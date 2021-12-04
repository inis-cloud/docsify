## 获取【用户】数据

> 通过该接口，你可以获取到全部的用户数据   
> 为了安全起见，该接口只返回非敏感数据，例如帐号、密码和邮箱等敏感数据已被屏蔽

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/users</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 否 | string | null | 登录密钥 | 拥有管理员权限将会显示敏感数据 |
| id | 否 | int | null | 用户ID | 存在则获取指定用户数据，否则获取全部 |
| limit | 否 | int | 5 | 数据数量 | 无 |
| page | 否 | int | 1 | 分页请求 | 无 |
| order | 否 | string | create_time asc | 排序方式 | 无 |
| cache | 否 | bool | true | 是否获取缓存数据 | 无 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/users',
  type:'GET',
  dataType:'JSON',
  success: (res) => {
	// 状态码 200 表示请求成功
	if(res.code === 200){
	  console.log(res.data)
	}else{
	  console.log(res)
	}
  }
})
</script>
```

#### ** axios **

```html
<!-- 导入axios -->
<script src="//unpkg.com/axios/dist/axios.min.js"></script>

<script>
axios.get('http://test.inis.cn/api/users').then((res) => {
  // 状态码 200 表示请求成功
  if(res.data.code == 200){
	console.log(res.data)
  }else{
	console.log(res)
  }
})
</script>
```

#### ** php **

```php
<?php
// 定义头部信息
header('content-type:application/json');
// API接口
$url  = 'http://test.inis.cn/api/users';

$curl = curl_init(); 
curl_setopt($curl,CURLOPT_URL,$url); 
curl_setopt($curl,CURLOPT_RETURNTRANSFER,true);
$data = curl_exec($curl); 
curl_close($curl);     

// 输出数据
echo $data;
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "code":200,
    "msg":"数据请求成功！",
    "data":{
        "page":1,
        "count":2,
        "data":[
            {
                "id":1,
                "nickname":"兔子",
                "sex":"女",
                "head_img":"https://api.inis.cn/storage/users/uid-1/my-head.gif",
                "description":"许一人以偏爱，尽此生之慷慨！",
                "status":1,
                "address_url":"https://inis.cn",
                "opt":{
                    "alipay":"//api.inis.cn/storage/users/pay/uid-1/alipay.jpg",
                    "login_auth":"76a2e43a1c60e999f919e1efe959872f",
                    "wechat_pay":"//api.inis.cn/storage/users/pay/uid-1/wechat-pay.png"
                },
                "create_time":"2021-05-09 16:14:51",
                "update_time":"2021-06-23 18:15:29",
                "last_login_time":"1624443329"
            },
            {
                "id":2,
                "nickname":"测试",
                "sex":"女",
                "head_img":"https://q.qlogo.cn/g?b=qq&amp;nk=97783391&amp;s=640",
                "description":"",
                "status":0,
                "address_url":"",
                "opt":{
                    "alipay":"//api.inis.cn/storage/users/pay/uid-1/alipay.jpg",
                    "login_auth":"0fc52baec5edc324bc989d58b941d992",
                    "wechat_pay":"//api.inis.cn/storage/users/pay/uid-1/wechat-pay.png"
                },
                "create_time":"2021-05-09 20:25:03",
                "update_time":"2021-06-23 01:00:38",
                "last_login_time":"1624281381"
            }
        ]
    }
}
```
</details>



## 用户【登录】接口

> 通过该接口，你可以开发用户登录接口   
> 登录成功之后，会返回一个 login-token 的加密字段，请务必保管好该字段   
> login-token 字段将用于判断权限操作   
> login-token 的有效期为 7200 秒，即2个小时，过期后需要重新登录

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/users</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| mode | 是 | string | 无 | login、register | 模式 | 选择接口模式 |
| account | 是 | string | 无 | 无 | 帐号 | 可以是帐号或邮箱 |
| password | 是 | string | 无 | 无 | 帐号 | 无 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/users',
  type:'GET',
  dataType:'JSON',
  data: {"account":"admin","password":"123456"},
  success: (res) => {
	// 状态码 200 表示请求成功
	if(res.code === 200){
	  console.log(res.data)
	}else{
	  console.log(res)
	}
  }
})
</script>
```

#### ** axios **

```html
<!-- 导入axios -->
<script src="//unpkg.com/axios/dist/axios.min.js"></script>

<script>
axios.post('http://test.inis.cn/api/users',{},{
    headers: {
        'Content-Type':'application/x-www-form-urlencoded'
    },
    params: {
        "mode"    : "login",
        "account" : "admin",
        "password":"123456"
    }
}).then(res=>{
    // 状态码 200 表示请求成功
    if(res.data.code == 200){
      console.log(res.data)
    }else{
      console.log(res)
    }
})
</script>
```

#### ** php **

```php
// 定义头部信息
header('content-type:application/json');

// 设置POST数据
$data = [
    'mode'        => 'login',
    'account'     => 'admin',
    'password'    => '123456',
];

// 提交接口
$url = 'http://test.inis.cn/api/users';

$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, $url);

curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);

curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, FALSE);

curl_setopt($ch, CURLOPT_POST, 1);

// 设置 user-agent 
curl_setopt($ch,CURLOPT_USERAGENT,'Mozilla/5.0 (Linux; Android 10; Mi9 Pro 5G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.117 Mobile Safari/537.36');

curl_setopt($ch, CURLOPT_POSTFIELDS, $data);

$output = curl_exec($ch);

curl_close($ch);

// 输出数据
echo $output;
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "code":200,
    "msg":"登录成功！",
    "data":{
        "login-token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJpbmlzIiwiYXVkIjpudWxsLCJpYXQiOjE2MjQ0NDc3NjMsIm5iZiI6MTYyNDQ0Nzc2MywiZXhwIjoxNjI0NDU0OTYzLCJ1aWQiOjF9.MVeR6Ke6L3jxkUpTM_QQXbq2N9uO6FMUvUW0AXkDGWA",
        "user":{
            "id":1,
            "nickname":"兔子",
            "sex":"女",
            "head_img":"https://api.inis.cn/storage/users/uid-1/my-head.gif",
            "description":"许一人以偏爱，尽此生之慷慨！",
            "status":1,
            "address_url":"https://inis.cn",
            "opt":{
                "alipay":"//api.inis.cn/storage/users/pay/uid-1/alipay.jpg",
                "login_auth":"ee4e34aae2564518d3574fa61598c27d",
                "wechat_pay":"//api.inis.cn/storage/users/pay/uid-1/wechat-pay.png"
            },
            "create_time":"2021-05-09 16:14:51",
            "update_time":"2021-06-23 19:29:23",
            "last_login_time":1624447763
        }
    }
}
```
</details>




## 用户【注册】接口

> 通过该接口，你可以开发用户注册接口   
> 注册成功后，系统会自动分配一个默认的随机头像   
> PS：默认使用邮箱登录，需要自定义帐号的，需要登录后自己设置

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/users</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| mode | 是 | string | 无 | login、register | 模式 | 选择接口模式 |
| nickname | 是 | string | 无 | 无 | 昵称 | 用于显示 |
| email | 是 | string | 无 | 无 | 邮箱 | 用于登录或找回密码 |
| password | 是 | string | 无 | 无 | 密码 | 无 |
| code | 是 | string | 无 | 无 | 验证码 | 用于校验邮箱是否存活，不区分大小写 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/users',
  type:'POST',
  dataType:'JSON',
  data: {"mode":"register","nickname":"张三","email":"zhangsan@qq.com",'password':'zhangsan..','code':'DASD21'},
  success: (res) => {
	// 状态码 200 表示请求成功
	if(res.code === 200){
	  console.log(res.data)
	}else{
	  console.log(res)
	}
  }
})
</script>
```

#### ** axios **

```html
<!-- 导入axios -->
<script src="//unpkg.com/axios/dist/axios.min.js"></script>

<script>
axios.post('http://test.inis.cn/api/users',{},{
    headers: {
        'Content-Type':'application/x-www-form-urlencoded'
    },
    params:{
        "mode"      : "register",
        "nickname"  : "张三",
        "email"     : "zhangsan@qq.com",
        'password'  : 'zhangsan..',
        'code'      : 'DASD21'
    }
  }).then(res=>{
    // 状态码 200 表示请求成功
    if(res.data.code == 200){
      console.log(res.data)
    }else{
      console.log(res)
    }
})
</script>
```

#### ** php **

```php
<?php
// 定义头部信息
header('content-type:application/json');

// 设置POST数据
$data = [
    'mode'        => "register",
    'email'       => "zhangsan@qq.com",
    'nickname'    => '张三',
    'password'    => 'zhangsan..',
    'code'        => 'code'
];

// 提交接口
$url = 'http://test.inis.cn/api/users';

$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, $url);

curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);

curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, FALSE);

curl_setopt($ch, CURLOPT_POST, 1);

// 设置 user-agent 
curl_setopt($ch,CURLOPT_USERAGENT,'Mozilla/5.0 (Linux; Android 10; Mi9 Pro 5G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.117 Mobile Safari/537.36');

curl_setopt($ch, CURLOPT_POSTFIELDS, $data);

$output = curl_exec($ch);

curl_close($ch);

// 输出数据
echo $output;
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "code":200,
    "msg":"ok",
    "data":{
        "email":"205211494@qq.com",
        "password":"123456"
    }
}
```
</details>





## 【新增或修改】用户

> 通过该接口，你可以新增或者修改用户数据   
> 前提条件是必须登录且拥有权限的用户   
> 只允许账号为 管理员 且 未被禁用 的账号进行提交   

!> 此接口虽与用户注册接口类似，但实则不一，该接口可用于后台用户管理

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/users</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 是 | string | null | 登录密钥 | 用于判断是否拥有权限（可以在参数或headers中提交，推荐header提交） |
| id | 否 | int | null | ID | ID存在为修改，反则新增 |
| account | 是 | string | null | 帐号 | 用于登录 |
| password | 否 | string | null | 密码 | 新增必须 |
| nickname | 否 | string | null | 昵称 | 新增必须 |
| sex | 否 | string | 保密 | 性别 | 无 |
| email | 否 | string | null | 邮箱 | 新增必须 |
| phone | 否 | string | null | 电话 | 无 |
| head_img | 否 | string | null | 头像地址 | 无 |
| description | 否 | string | null | 描述 | 无 |
| status | 否 | int | 1 | 状态 | 0表示禁用，1表示启用 |
| level | 否 | string | user | 权限 | admin表示管理员，user表示用户 |
| address_url | 否 | string | null | 用户网址 | 无 |
| remarks | 否 | string | null | 备注 | 无 |
| longtext | 否 | longtext | null | 自定义字段 | 无格式要求 |
| code | 否 | string | null | 验证码 | 仅在需要修改个人邮箱需要提交，系统会自动往修改的邮箱发送验证码 |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 发表按钮
$('#btn-save').on('click', () => {
	
	let token       = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...';
    let id          = 1;
    let nickname    = '测试';
    let password	= '123456';

    let data = {'login-token':token, id, nickname, password};

    $.ajax({
        url:'http://test.inis.cn/api/users',
        type:'POST',
        data:data,
        dataType:'JSON',
        success: (res) => {
            if(res.code === 200){
                console.log(res.data)
            }else{
                console.log(res)
            }
        }
    })
})
</script>
```

#### ** axios **

```html
<!-- 导入axios -->
<script src="//unpkg.com/axios/dist/axios.min.js"></script>

<script>
axios.post('http://test.inis.cn/api/users',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		"login-token"  : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
		id             : 1,
		nickname       : '测试',
		password       : '123456',
	}
}).then(res=>{
  // 状态码 200 表示请求成功
  if(res.data.code == 200){
	console.log(res.data)
  }else{
	console.log(res)
  }
})
</script>
```

#### ** php **

```php
<?php
// 定义头部信息
header('content-type:application/json');

// 设置POST数据
$data = [
    'login-token' => "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
    'id'          => 1,
    'nickname'    => '测试',
    'password'    => '123456',
];

// 提交接口
$url = 'http://test.inis.cn/api/users';

$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, $url);

curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);

curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, FALSE);

curl_setopt($ch, CURLOPT_POST, 1);

// 设置 user-agent 
curl_setopt($ch,CURLOPT_USERAGENT,'Mozilla/5.0 (Linux; Android 10; Mi9 Pro 5G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.117 Mobile Safari/537.36');

curl_setopt($ch, CURLOPT_POSTFIELDS, $data);

$output = curl_exec($ch);

curl_close($ch);

// 输出数据
echo $output;
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "code": 200,
    "msg": "ok",
    "data": []
}
```
</details>




## 【删除】用户

> 通过该接口，你可以删除一条或者多条文章数据   
> 前提条件是必须登录且拥有权限的用户   
> 只允许账号为 管理员 且 未被禁用 的账号进行提交   

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/users</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 是 | string | 无 | 无 | 登录密钥 | 用于判断是否拥有权限（可以在参数或headers中提交，推荐header提交） |
| mode | 是 | string | null | remove | 模式 | 无 |
| id | 否 | int、string | null | 无 | 友链ID | 支持批量，用 , 号隔开多个ID |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 发表按钮
$('#btn-save').on('click', () => {
	
	let token       = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...';
    let mode        = 'delete';
    let id          = '1';

    let data = {'login-token':token, mode, id};

    $.ajax({
          url:'http://test.inis.cn/api/users',
          type:'POST',
          data:data,
          dataType:'JSON',
          success: (res) => {
              if(res.code === 200){
                console.log(res.data)
              }else{
                console.log(res)
              }
          }
      })
  })
</script>
```

#### ** axios **

```html
<!-- 导入axios -->
<script src="//unpkg.com/axios/dist/axios.min.js"></script>

<script>
axios.post('http://test.inis.cn/api/users',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		"login-token"  : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
		mode           : 'delete',
		id             : '1,2,3',
	}
}).then(res=>{
  // 状态码 200 表示请求成功
  if(res.data.code == 200){
	console.log(res.data)
  }else{
	console.log(res)
  }
})
</script>
```

#### ** php **

```php
<?php
// 定义头部信息
header('content-type:application/json');

// 设置POST数据
$data = [
    'login-token'  => "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
    mode           => 'delete',
	id             => '1',
];

// 提交接口
$url = 'http://test.inis.cn/api/users';

$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, $url);

curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);

curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, FALSE);

curl_setopt($ch, CURLOPT_SSL_VERIFYHOST, FALSE);

curl_setopt($ch, CURLOPT_POST, 1);

// 设置 user-agent 
curl_setopt($ch,CURLOPT_USERAGENT,'Mozilla/5.0 (Linux; Android 10; Mi9 Pro 5G) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.117 Mobile Safari/537.36');

curl_setopt($ch, CURLOPT_POSTFIELDS, $data);

$output = curl_exec($ch);

curl_close($ch);

// 输出数据
echo $output;
```

<!-- tabs:end -->

<details>
<summary>请求成功返回的数据结构</summary>

```json
{
    "code": 200,
    "msg": "ok",
    "data": []
}
```
</details>
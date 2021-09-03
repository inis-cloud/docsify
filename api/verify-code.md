### 验证码【生成】

> 通过该接口，你可以创建一个验证码   
> PS：创建的验证码结果，会发送到对应的邮箱中，发送成功的前提是有在后台配置邮箱信息，并且信息正确

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/verify-code</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| email | 是 | string | null | null | 邮箱 |
| mode | 否 | string | null | create、check | 创建和校验 |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 发表评论按钮
$('#btn-save').on('click', () => {
	
    let mode  = "create";
	let email = 'racns@qq.com';

    let data = {mode,email};

    $.ajax({
          url:'http://api.inis.cc/api/verify-code',
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
axios.post('http://api.inis.cc/api/verify-code',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		mode  : 'create',
		email : 'racns@qq.com'
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
    'mode'    => 'create',
    'email'   => 'racns@qq.com',
];

// 提交评论接口
$url = 'http://api.inis.cc/api/verify-code';

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
    "msg":"验证码已发送至邮箱5分钟内有效！",
    "data":[

    ]
}
```
</details>





### 验证码【校验】

> 通过该接口，你可以创建一个验证码   
> PS：验证码一旦校验成功，系统将会自动删除数据库中的验证码记录，这意味着，单个验证码只能使用一次

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/verify-code</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| code | 是 | string | null | null | 验证码 |
| email | 是 | string | null | null | 邮箱 |
| mode | 否 | string | null | create、check | 创建和校验 |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 发表评论按钮
$('#btn-save').on('click', () => {
	
    let mode  = "check";
	let code  = 'FJGMH2';
	let email = 'racns@qq.com';

    let data = {mode,email,code};

    $.ajax({
          url:'http://api.inis.cc/api/verify-code',
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
axios.post('http://api.inis.cc/api/verify-code',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		mode  : 'check',
		code  : 'FJGMH2',
		email : 'racns@qq.com'
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
    'mode'    => 'check',
    'code'    => 'FJGMH2',
    'email'   => 'racns@qq.com',
];

// 提交评论接口
$url = 'http://api.inis.cc/api/verify-code';

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
    "msg": "验证码有效！",
    "data": []
}
```
</details>
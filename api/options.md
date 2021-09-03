### 获取【全部】配置信息

> 通过该接口，你可以获取到全部的公开配置信息

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/options</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://api.inis.cc/api/options',
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
axios.get('http://api.inis.cc/api/options').then((res) => {
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
$url  = 'http://api.inis.cc/api/options';

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
    "msg":"数据请求成功",
    "data":{
        "title":"INIS API",
        "keywords":"API,INIS",
        "description":"INIS API SYSTEM",
        "copy":"这个是备案信息",
        "site_ico":"http://inis.racns.com/img/userHead.gif",
        "site_img":"http://inis.racns.com/img/userHead.gif",
        "site_url":"http://inis.cc",
        "theme":"sidebar-enable",
		... ...
    }
}
```
</details>




### 获取【一条】配置信息

> 通过该接口，你可以获取指定友链的配置信息和非公开的配置信息

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/options</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| key | 否 | string | 无 | 键 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://api.inis.cc/api/options',
  type:'GET',
  dataType:'JSON',
  data: {"key":"title"}
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
axios.get('http://api.inis.cc/api/options',{
    params:{"key":"title"}  
  }).then((res) => {
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
$url  = 'http://api.inis.cc/api/options?key=title';

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
    "msg":"数据请求成功",
    "data":{
        "keys":"title",
        "value":"INIS API"
    }
}
```
</details>






### 【新增或修改】配置

> 通过该接口，你可以新增或者修改配置数据   
> 前提条件是必须登录且拥有权限的用户   
> 只允许账号为 管理员 且 未被禁用 的账号进行提交   

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/options</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 是 | string | 无 | 登录密钥 | 用于判断是否拥有权限 |
| keys | 是 | string | null | 类似于ID，唯一 | 库里已有表示修改，没有表示新增 |
| value | 否 | string | null | longtext字段 | 可以存储超长的数据 |
| opt | 否 | object | null | 存储JSON数据 | 可以提交一个对象格式的数据或者类似对象格式的字符串 |
| cover | 否 | bool | false | 是否覆盖数据 | 默认情况下为替换数据，但不覆盖数据 |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 提交
$('#btn-save').on('click', () => {
	
	let token       = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...';
    let keys        = 'test';
    let value       = '这是一个测试的内容！';
    let opt	        = {test:"这是一个测试的JSON", array:"1,2,3"};   // 对象格式

    let data = {'login-token':token, keys, value, opt};

    $.ajax({
          url:'http://api.inis.cc/api/options',
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
axios.post('http://api.inis.cc/api/options',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		"login-token"  : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
		keys           : 'test',
		value          : '这是一个测试的内容！',
		opt            : '{test:"这是一个测试的JSON", array:"1,2,3"}',  // 对象格式的字符串
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
    keys           => 'test',
	value          => '这是一个测试的内容！',
	opt            => ["test"=>"这是一个测试的JSON", "array"=>"1,2,3"],  // PHP中，这里可以是一个数组或者对象格式的字符串
];

// 提交接口
$url = 'http://api.inis.cc/api/options';

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





### 【删除】配置

> 通过该接口，你可以删除一条或者多条文章数据   
> 前提条件是必须登录且拥有权限的用户   
> 只允许账号为 管理员 且 未被禁用 的账号进行提交   

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/options</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 是 | string | 无 | 无 | 登录密钥 | 用于判断是否拥有权限 |
| mode | 是 | string | null | remove | 模式 | 无 |
| keys | 否 | string | null | 无 | 类似于ID，唯一 | 无 |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 发表评论按钮
$('#btn-save').on('click', () => {
	
	let token       = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...';
    let mode        = 'delete';
    let keys        = 'test';

    let data = {'login-token':token, mode, keys};

    $.ajax({
          url:'http://api.inis.cc/api/options',
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
axios.post('http://api.inis.cc/api/options',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		"login-token"  : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
		mode           : 'delete',
		keys           : 'test',
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
	keys           => 'test',
];

// 提交接口
$url = 'http://api.inis.cc/api/options';

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
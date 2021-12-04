## 获取【全部】友链数据

> 通过该接口，你可以获取到全部的友链数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/links</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| limit | 否 | int | 5 | 数据数量 |
| page | 否 | int | 1 | 分页请求 |
| order | 否 | string | create_time desc | 排序方式 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/links',
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
axios.get('http://test.inis.cn/api/links').then((res) => {
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
$url  = 'http://test.inis.cn/api/links';

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
        "data":[
            {
                "id":1,
                "name":"兔子",
                "url":"http://inis.cn",
                "head_img":"https://racns.com/usr/images/userHead.gif",
                "description":"许一人以偏爱，尽此生之慷慨！",
                "sort":"全局友链",
                "is_show":1,
                "opt":null,
                "create_time":"2020-11-07 15:19:30",
                "update_time":"2020-11-09 21:30:00"
            },
            {
                "id":4,
                "name":"Empty",
                "url":"http://inzj.cn",
                "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=804966813&amp;s=640",
                "description":"某Empty",
                "sort":"全局友链",
                "is_show":1,
                "opt":null,
                "create_time":"2020-11-09 11:10:22",
                "update_time":"2021-01-31 15:12:20"
            },
            {
                "id":5,
                "name":"谦夏",
                "url":"javascript:void(0);",
                "head_img":"http://q1.qlogo.cn/g?b=qq&amp;nk=1589472813&amp;s=640",
                "description":"谦夏",
                "sort":"全局友链",
                "is_show":1,
                "opt":null,
                "create_time":"2020-11-09 12:56:23",
                "update_time":"2020-11-26 15:26:45"
            }
        ],
        "page":1,
        "count":3
    }
}
```
</details>




## 获取【一条】友链数据

> 通过该接口，你可以获取指定友链的详细数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/links</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| id | 否 | int | 无 | 友链ID |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/links',
  type:'GET',
  dataType:'JSON',
  data: {"id":1},
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
axios.get('http://test.inis.cn/api/links',{
    params:{ "id":1 }
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
// API接口
$url  = 'http://test.inis.cn/api/links?id=1';

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
        "id":1,
        "name":"兔子",
        "url":"https://inis.cn",
        "head_img":"https://racns.com/usr/images/userHead.gif",
        "description":"许一人以偏爱，尽此生之慷慨！",
        "sort":"全局友链",
        "is_show":1,
        "create_time":"2020-11-07 15:19:30",
        "update_time":"2020-11-09 21:30:00"
    }
}
```
</details>




## 【SQL】接口

> 通过该接口，你可以自己编写SQL语法获取更多自定义的数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/links/sql</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| limit | 否 | int | 5 | 数据数量 |
| page | 否 | int | 1 | 分页请求 |
| order | 否 | string | create_time desc | 排序方式 |
| where | 否 | string | 无 | 条件查询 |
| whereOr | 否 | string | 无 | 条件查询 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<br>
<details>
<br>
<summary class="violet">字段说明</summary>

| 参数名称 | 语法 | 说明 |
| :---- | :---- | :---- |
| where | id=1;is_show=1; <span style="color:red">或</span> id=1 and is_show=1 | 用 ; 号或 and 隔开多个参数 |
| whereOr | sort,like,%全局友链%;is_show,=,1; | 用 ; 号隔开多个查询条件，每个查询条件有三个参数，用 , 号隔开 |

</details>

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/links/sql',
  type:'GET',
  dataType:'JSON',
  data:{
    "limit":3,
    "where":"id=1;is_show=1;"
  },
  success:function (res) {
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
axios.get('http://test.inis.cn/api/links/sql',{
    params:{
      "order"  : "id acs",
      "whereOr": "sort,like,%全局友链%",    // 可以实现模糊搜索
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
// API接口
$url  = 'http://test.inis.cn/api/links/sql?where=id=1;is_show=1;';

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
    "msg":"ok",
    "data":{
        "page":1,
        "count":1,
        "data":[
            {
                "id":1,
                "name":"兔子",
                "url":"http://inis.cn",
                "head_img":"https://racns.com/usr/images/userHead.gif",
                "description":"许一人以偏爱，尽此生之慷慨！",
                "sort":"全局友链",
                "is_show":1,
                "opt":null,
                "create_time":"2020-11-07 15:19:30",
                "update_time":"2021-03-24 12:45:22"
            }
        ]
    }
}
```
</details>





## 【新增或修改】友联

> 通过该接口，你可以新增或者修改友联数据   
> 前提条件是必须登录且拥有权限的用户   
> 只允许账号为 管理员 且 未被禁用 的账号进行提交   

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/links</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 是 | string | 无 | 登录密钥 | 用于判断是否拥有权限（可以在参数或headers中提交，推荐header提交） |
| sort_id | 是 | string | null | 友链分组ID | 无 |
| id | 否 | int | null | ID | 提交ID为修改，反则新增 |
| named | 否 | string | null | 该字段等于name字段 | 由于TP6会抢占name参数，所以用named代替name |
| url | 否 | string | null | 友链链接 | 无 |
| head_img | 否 | string | null | 头像链接 | 无 |
| description | 否 | string | null | 友链描述 | 无 |
| is_show | 否 | int | 1 | 是否显示 | 无 |


<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 发表评论按钮
$('#btn-save').on('click', () => {
	
	let token       = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...';
    let sort_id     = 1;
    let named       = '兔子';
    let url	        = '//inis.cn';
	let head_img	= '//q.qlogo.cn/g?b=qq&nk=97783391&s=640';
	let description = '萌卜兔';
	let is_show 	= 1;

    let data = {'login-token':token, sort_id, named, url, head_img, description, is_show};

    $.ajax({
          url:'http://test.inis.cn/api/links',
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
axios.post('http://test.inis.cn/api/links',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		"login-token"  : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
		sort_id        : 1,
		named          : '兔子',
		url            : '//inis.cn',
		head_img       : '//q.qlogo.cn/g?b=qq&nk=97783391&s=640',
		description    : '萌卜兔',
		is_show        : 1
		
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
    'sort_id'     => 1,
    'named'       => '兔子',
    'head_img'    => '//q.qlogo.cn/g?b=qq&nk=97783391&s=640',
    'description' => '萌卜兔',
    'is_show'     => 1
];

// 提交评论接口
$url = 'http://test.inis.cn/api/links';

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






## 【删除】友链

> 通过该接口，你可以删除一条或者多条文章数据   
> 前提条件是必须登录且拥有权限的用户   
> 只允许账号为 管理员 且 未被禁用 的账号进行提交   

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/links</p>

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
// 发表评论按钮
$('#btn-save').on('click', () => {
	
	let token       = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...';
    let mode        = 'delete';
    let id          = '1';

    let data = {'login-token':token, mode, id};

    $.ajax({
          url:'http://test.inis.cn/api/links',
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
axios.post('http://test.inis.cn/api/links',{},{
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
$url = 'http://test.inis.cn/api/links';

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
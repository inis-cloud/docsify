## 获取【全部】标签数据

> 通过该接口，你可以获取到全部的标签数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/tag</p>

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
  url:'http://test.inis.cn/api/tag',
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
axios.get('http://test.inis.cn/api/tag').then((res) => {
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
$url  = 'http://test.inis.cn/api/tag';

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
                "id":91,
                "name":"标签2",
                "is_show":1,
                "expand":{
                    "count":0,
                    "color":"success"
                },
                "opt":null,
                "create_time":"2021-01-20 16:08:03",
                "update_time":"2021-01-20 16:08:31"
            },
    		... ...
    		{...},
    		{...}
        ],
        "page":1,
        "count":3
    }
}
```
</details>




## 获取【标签下】的文章数据

> 通过该接口，你可以获取指定标签下的文章数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/tag</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| id | 否 | int | 无 | 标签ID |
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
  url:'http://test.inis.cn/api/tag',
  type:'GET',
  dataType:'JSON',
  data: {"id":89},
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
axios.get('http://test.inis.cn/api/tag',{
    params:{ "id":89 }
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
$url  = 'http://test.inis.cn/api/tag?id=89';

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

> `expand` 内的数据为后端优化并处理过的数据，请优先使用 `expand` 内的数据

```json
{
    "code":200,
    "msg":"数据请求成功！",
    "data":{
        "id":102,
        "name":"标签5",
        "is_show":1,
        "opt":null,
        "expand":{
            "page":1,
            "count":2,
            "data":[
                {
                    "id":66,
                    "title":"新的测试",
                    "description":"&lt;p&gt;&lt;br&gt;&lt;/p&gt;",
                    "is_top":0,
                    "is_show":1,
                    "img_src":"https://picabstract-preview-ftn.weiyun.com/ftn_pic_abs_v3/6e111d4cfec8eb6ff4700a62cab984ec31420655d279b17fda9ef19fbb09005e93c393b40b4da61c765ca4b1f2e51df4?pictype=scale&amp;from=30013&amp;version=3.3.3.3&amp;uin=1211515059&amp;fname=74364959_p0_master1200.jpg&amp;size=750",
                    "views":708,
                    "font_count":0,
                    "sort_id":"|14|",
                    "tag_id":"|102|",
                    "users_id":1,
                    "expand":{
                        "author":{
                            "nickname":"兔子",
                            "head_img":"https://q.qlogo.cn/g?b=qq&amp;nk=97783391&amp;s=640",
                            "email":"racns@qq.com",
                            "address_url":"https://inis.cn",
                            "description":"许一人以偏爱，尽此生之慷慨！",
                            "pay":{
                                "alipay":"//api.inis.cn/storage/users/pay/uid-1/alipay.jpg",
                                "qq_pay":"//api.inis.cn/storage/users/pay/uid-1/qq_pay.png",
                                "wechat_pay":"//api.inis.cn/storage/users/pay/uid-1/wechat-pay.png"
                            }
                        },
                        "tag":[
                            {
                                "id":102,
                                "name":"标签5",
                                "color":"light"
                            }
                        ],
                        "sort":[
                            {
                                "id":14,
                                "name":"ThinkPHP6"
                            }
                        ],
                        "comments":13,
                        "img_src":"https://picabstract-preview-ftn.weiyun.com/ftn_pic_abs_v3/6e111d4cfec8eb6ff4700a62cab984ec31420655d279b17fda9ef19fbb09005e93c393b40b4da61c765ca4b1f2e51df4?pictype=scale&amp;from=30013&amp;version=3.3.3.3&amp;uin=1211515059&amp;fname=74364959_p0_master1200.jpg&amp;size=750"
                    },
                    "opt":null,
                    "delete_time":null,
                    "create_time":"2020-11-21 15:16:28",
                    "update_time":"2021-07-24 23:17:01",
                    "last_update_time":"1624610032"
                },
                ... ...
                ... ...
            ]
        },
        "create_time":"2021-03-15 17:41:01",
        "update_time":"2021-06-12 21:46:11"
    }
}
```
</details>




## 【SQL】接口

> 通过该接口，你可以自己编写SQL语法获取更多自定义的数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/tag/sql</p>

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
| where | di=102;is_show=1; <span style="color:red">或</span> id=102 and is_show=1 | 用 ; 号或 and 隔开多个参数 |
| whereOr | name,like,%标签%;is_show,=,1; | 用 ; 号隔开多个查询条件，每个查询条件有三个参数，用 , 号隔开 |

</details>

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/tag/sql',
  type:'GET',
  dataType:'JSON',
  data:{
    "limit":3,
    "where":"id=102;is_show=1;"
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
axios.get('http://test.inis.cn/api/tag/sql',{
    params:{
      "order"  : "id acs",
      "whereOr": "name,like,%标签%",    // 可以实现模糊搜索
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
$url  = 'http://test.inis.cn/api/tag/sql?where=id=102;is_show=1;';

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

> `expand` 内的数据为后端优化并处理过的数据，请优先使用 `expand` 内的数据

```json
{
    "code":200,
    "msg":"ok",
    "data":{
        "page":1,
        "count":1,
        "data":[
            {
                "id":102,
                "name":"标签5",
                "is_show":1,
                "opt":null,
                "expand":{
                    "count":2,
                    "color":"dark"
                },
                "create_time":"2021-03-15 17:41:01",
                "update_time":"2021-03-23 14:51:05"
            }
        ]
    }
}
```
</details>




## 【新增或修改】标签

> 通过该接口，你可以新增或者修改标签数据   
> 前提条件是必须登录且拥有权限的用户   
> 只允许账号为 未被禁用 的账号进行提交   

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/tag</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 是 | string | 无 | 登录密钥 | 用于判断是否拥有权限（可以在参数或headers中提交，推荐header提交） |
| id | 否 | int | null | 标签ID | 存在则修改，反之新增 |
| named | 否 | string | null | 该字段等于name字段 | 由于TP6会抢占name参数，所以用named代替name |
| is_show | 否 | string | 1 | 是否显示 | 0表示不显示 |
| opt | 否 | string | null | JSON字段 | 如：{"test":"这是一个JSON字段"} |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 发表评论按钮
$('#btn-save').on('click', () => {
	
	let token       = 'eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...';
    let named       = '新增标签';
    let opt         = '{"test":"这是一个JSON字段"}';

    let data = {'login-token':token, named, opt};

    $.ajax({
          url:'http://test.inis.cn/api/article',
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
axios.post('http://test.inis.cn/api/article',{},{
	headers: {
		'Content-Type':'application/x-www-form-urlencoded'
	},
	params: {
		"login-token"  : "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOi...",
		named          : '新增标签',
		opt            : '{"test":"这是一个JSON字段"}',
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
    named          => '新增标签',
	opt            => '{"test":"这是一个JSON字段"}',
];

// 提交接口
$url = 'http://test.inis.cn/api/article';

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





## 【删除】标签

> 通过该接口，你可以删除一条或者多条标签数据   
> 前提条件是必须登录且拥有权限的用户   
> 只允许账号为 未被禁用 的账号进行提交   

<p class="api-request post" data-lang="API"><em></em>http://[域名]/api/tag</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| login-token | 是 | string | 无 | 无 | 登录密钥 | 用于判断是否拥有权限（可以在参数或headers中提交，推荐header提交） |
| mode | 是 | string | null | remove | 模式 | 无 |
| id | 否 | string、array | null | 无 | 标签ID | 可以用 , 号隔开多个ID |


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
    let id          = '1,2,3';

    let data = {'login-token':token, mode, id};

    $.ajax({
          url:'http://test.inis.cn/api/tag',
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
axios.post('http://test.inis.cn/api/tag',{},{
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
	id             => '1,2,3',
];

// 提交接口
$url = 'http://test.inis.cn/api/tag';

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
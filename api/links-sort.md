## 获取【全部】友链分类数据

> 通过该接口，你可以获取到全部的友链分类数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/links-sort</p>

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
  url:'http://test.inis.cn/api/links-sort',
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
axios.get('http://test.inis.cn/api/links-sort').then((res) => {
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
$url  = 'http://test.inis.cn/api/links-sort';

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
        "data":[
            {
                "id":3,
                "name":"推荐友链",
                "slug":"sell",
                "description":"这个分组下的友链会在推荐页显示",
                "is_show":1,
                "expand":{
                    "count":0,
                    "color":"info"
                },
                "opt":null,
                "create_time":"2020-11-07 17:00:35",
                "update_time":"2020-11-07 17:00:35"
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




## 获取【一个】友链分类下的数据

> 通过该接口，你可以获取指定友链分类的详细数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/links-sort</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| id | 否 | int | 无 | 友链分类ID |
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
  url:'http://test.inis.cn/api/links-sort',
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
axios.get('http://test.inis.cn/api/links-sort',{
    params:{ "id":1 }
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
$url  = 'http://test.inis.cn/api/links-sort?id=1';

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
    "msg":"数据请求成功",
    "data":{
        "id":1,
        "name":"全局友链",
        "slug":"global",
        "description":"这个分组下的友链将会在首页显示",
        "is_show":1,
        "expand":{
            "count":3,
            "links":[
                {
                    "id":1,
                    "name":"兔子",
                    "url":"http://inis.cn",
                    "head_img":"https://racns.com/usr/images/userHead.gif",
                    "description":"许一人以偏爱，尽此生之慷慨！",
                    "is_show":1,
                    "create_time":"2020-11-07 15:19:30",
                    "update_time":"2020-11-09 21:30:00"
                },
				... ...
				{...},
				{...}
            ]
        },
        "create_time":"2020-11-07 16:58:57",
        "update_time":"2020-11-07 16:58:57"
    }
}
```
</details>




## 【SQL】接口

> 通过该接口，你可以自己编写SQL语法获取更多自定义的数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/links-sort/sql</p>

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
| where | id=1;name=推荐友链 <span style="color:red">或</span> id=1 and name=推荐友链 | 用 ; 号或 and 隔开多个参数 |
| whereOr | name,like,%友链%;id,=,1; | 用 ; 号隔开多个查询条件，每个查询条件有三个参数，用 , 号隔开 |

</details>

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/links-sort/sql',
  type:'GET',
  dataType:'JSON',
  data:{
    "where":"id=1;name=全局友链;"
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
axios.get('http://test.inis.cn/api/links-sort/sql',{
    params:{
      "order"  : "id acs",
      "whereOr": "name,like,%友链%",    // 可以实现模糊搜索
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
$url  = 'http://test.inis.cn/api/links-sort/sql?whereOr=name,like,%友链%';

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
                "id":1,
                "name":"全局友链",
                "slug":"global",
                "description":"这个分组下的友链将会在首页显示",
                "is_show":1,
                "expand":{
                    "count":4,
                    "color":"success"
                },
                "opt":null,
                "create_time":"2020-11-07 16:58:57",
                "update_time":"2020-11-07 16:58:57"
            }
        ]
    }
}
```
</details>
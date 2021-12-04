## 获取【全部】文章分类数据

> 通过该接口，你可以获取到文章分类的全部数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/article-sort</p>

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
  url:'http://test.inis.cn/api/article-sort',
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
axios.get('http://test.inis.cn/api/article-sort').then((res) => {
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
$url  = 'http://test.inis.cn/api/article-sort';

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
                "id":1,
                "name":"Vue",
                "slug":"vue",
                "description":"属于Vue的文章分类",
                "is_show":0,
                "expand":{
                    "count":3
                },
                "opt":null,
                "create_time":"2020-10-01 15:26:47",
                "update_time":"2020-10-01 15:26:47"
            },
            {
                "id":14,
                "name":"ThinkPHP6",
                "slug":"PHP",
                "description":"ThinkPHP6",
                "is_show":1,
                "expand":{
                    "count":4
                },
                "opt":null,
                "create_time":"2020-11-04 14:16:45",
                "update_time":"2020-11-05 11:45:14"
            },
            {
                "id":20,
                "name":"HTML+CSS",
                "slug":"web",
                "description":"HTML+CSS",
                "is_show":1,
                "expand":{
                    "count":0
                },
                "opt":null,
                "create_time":"2020-11-07 16:17:31",
                "update_time":"2020-11-07 16:17:31"
            }
        ],
        "page":1,
        "count":3
    }
}
```
</details>




## 获取【分类下】的文章数据

> 通过该接口，你可以获取到分类下的文章数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/article-sort</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| id | 否 | int | 无 | 文章分类ID |
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
  url:'http://test.inis.cn/api/article-sort',
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
axios.get('http://test.inis.cn/api/article-sort',{
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
$url  = 'http://test.inis.cn/api/article-sort?id=1';

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
        "name":"Vue",
        "slug":"vue",
        "description":"属于Vue的文章分类",
        "is_show":0,
        "expand":{
            "count":2,
            "article":[
                {
                    "id":1,
                    "title":"inis系统",
                    "description":"这是一个描述",
                    "is_top":0,
                    "is_show":1,
                    "img_src":"https://racns.com/usr/uploads/2020/09/3993362207.jpg",
                    "views":698,
                    "font_count":10000,
                    "sort_id":"|1|14|",
                    "tag_id":"",
                    "users_id":1,
                    "expand":{
                        "sort":[
                            {
                                "id":1,
                                "name":"Vue"
                            },
                            {
                                "id":14,
                                "name":"ThinkPHP6"
                            }
                        ],
                        "author":{
                            "nikename":"兔子",
                            "head_img":"http://inis.racns.com/img/userHead.gif",
                            "email":"racns@qq.com",
                            "address_url":"https://inis.cn",
                            "description":"许一人以偏爱，尽此生之慷慨！"
                        },
                        "comments":7
                    },
                    "create_time":"2020-10-01 15:26:47",
                    "update_time":"2020-12-18 13:23:01"
                },
				... ...
				{...},
				{...}
            ]
        },
        "create_time":"2020-10-01 15:26:47",
        "update_time":"2020-10-01 15:26:47"
    }
}
```
</details>




## 【SQL】接口

> 通过该接口，你可以自己编写SQL语法获取更多自定义的数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/article-sort/sql</p>

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
| whereOr | name,like,%inis系统%;is_show,=,1; | 用 ; 号隔开多个查询条件，每个查询条件有三个参数，用 , 号隔开 |

</details>

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/article-sort/sql',
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
axios.get('http://test.inis.cn/api/article-sort/sql',{
    params:{
      "order"  : "id acs",
      "whereOr": "name,like,%inis系统%",    // 可以实现模糊搜索
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
$url  = 'http://test.inis.cn/api/article-sort/sql?where=id=1;is_show=1;';

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
        "count":2,
        "data":[
            {
                "id":20,
                "name":"HTML+CSS",
                "slug":"web",
                "description":"HTML+CSS",
                "is_show":1,
                "expand":{
                    "count":0
                },
                "opt":null,
                "create_time":"2020-11-07 16:17:31",
                "update_time":"2021-02-26 14:53:18"
            },
            {
                "id":14,
                "name":"ThinkPHP6",
                "slug":"PHP",
                "description":"ThinkPHP6",
                "is_show":1,
                "expand":{
                    "count":3
                },
                "opt":null,
                "create_time":"2020-11-04 14:16:45",
                "update_time":"2020-11-05 11:45:14"
            }
        ]
    }
}
```
</details>
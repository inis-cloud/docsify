## 统计【总】数据 <span class="text-primary ml-1">[ new ]</span>

> 通过该接口，你可以获取到聚合统计的数据
> 改接口返回的是数据统计的总数量

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/group</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| field | 否 | string | [全部] | links、article、users、page、comments、music、tag、linksSort、articleSort、other | 选择显示数据，用英文 , 号隔开多个数据 |
| day | 否 | int | null | null | 需要显示X天内的数据 |
| detail | 否 | bool | false | true、false | 是否显示详细数据 |
| limit | 否 | int | 5 | null | 数据数量 |
| page | 否 | int | 1 | null | 分页请求 |
| order | 否 | string | null | create_time desc | 排序方式 |
| cache | 否 | bool | true | true、false | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/group',
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
axios.get('http://test.inis.cn/api/group').then((res) => {
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
$url  = 'http://test.inis.cn/api/group';

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
        "links":{
            "count":4
        },
        "article":{
            "count":9
        },
        "users":{
            "count":25
        },
        "page":{
            "count":2
        },
        "comments":{
            "count":142
        },
        "music":{
            "count":2
        },
        "tag":{
            "count":5
        },
        "linkssort":{
            "count":3
        },
        "articlesort":{
            "count":3
        }
    }
}
```
</details>




## 统计【详细】数据 <span class="text-primary ml-1">[ new ]</span>

> 通过该接口，你可以获取到聚合统计的数据
> 改接口返回的是数据统计的总数量

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/group</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| mode | 否 | string | count | detail、visit | detail表示获取详细的统计数据，visit表示访客数据 | 详细到每天新增了多少 |
| field | 否 | string | [全部] | links、article、users、comments、tag、visit | 选择显示数据，用英文 , 号隔开多个数据 | 当mode=visit时，该字段无效 |
| date | 否 | string | null | null | 具体时间内的数据（日期格式） | 两个参数，用英文 , 号隔开（如：2021-8-1,2021-8-7），参数二为空自动获取当前的时间 |
| timestamp | 否 | string | null | null | 具体时间内的数据（时间戳格式，优先级比date高） | 两个参数，用英文 , 号隔开（如：1627792201,1628265600），参数二为空自动获取当前的时间戳 |
| cache | 否 | bool | true | true、false | 是否获取缓存数据 | 无 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/group',
  type:'GET',
  dataType:'JSON',
  data: {"mode":"detail"},
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
axios.get('http://test.inis.cn/api/group',{
    params:{ "mode":"detail" }
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
$url  = 'http://test.inis.cn/api/group?mode=detail';

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
        "users":[
            [
                "2021-08-06",
                0
            ],
            [
                "2021-08-07",
                3
            ],
            [
                "2021-08-08",
                1
            ],
            [
                "2021-08-09",
                0
            ],
            [
                "2021-08-10",
                0
            ],
            [
                "2021-08-11",
                0
            ],
            [
                "2021-08-12",
                1
            ]
        ],
        "article":[
            [
                "2021-08-06",
                0
            ],
            [
                "2021-08-07",
                0
            ],
            [
                "2021-08-08",
                0
            ],
            [
                "2021-08-09",
                0
            ],
            [
                "2021-08-10",
                0
            ],
            [
                "2021-08-11",
                0
            ],
            [
                "2021-08-12",
                0
            ]
        ],
        "comments":[
            [
                "2021-08-06",
                0
            ],
            [
                "2021-08-07",
                16
            ],
            [
                "2021-08-08",
                0
            ],
            [
                "2021-08-09",
                1
            ],
            [
                "2021-08-10",
                0
            ],
            [
                "2021-08-11",
                0
            ],
            [
                "2021-08-12",
                0
            ]
        ],
        "links":[
            [
                "2021-08-06",
                0
            ],
            [
                "2021-08-07",
                0
            ],
            [
                "2021-08-08",
                0
            ],
            [
                "2021-08-09",
                0
            ],
            [
                "2021-08-10",
                0
            ],
            [
                "2021-08-11",
                0
            ],
            [
                "2021-08-12",
                0
            ]
        ],
        "tag":[
            [
                "2021-08-06",
                0
            ],
            [
                "2021-08-07",
                0
            ],
            [
                "2021-08-08",
                0
            ],
            [
                "2021-08-09",
                0
            ],
            [
                "2021-08-10",
                0
            ],
            [
                "2021-08-11",
                0
            ],
            [
                "2021-08-12",
                0
            ]
        ],
        "visit":[
            [
                "2021-08-06",
                0
            ],
            [
                "2021-08-07",
                0
            ],
            [
                "2021-08-08",
                0
            ],
            [
                "2021-08-09",
                0
            ],
            [
                "2021-08-10",
                0
            ],
            [
                "2021-08-11",
                3
            ],
            [
                "2021-08-12",
                6
            ]
        ]
    }
}
```
</details>
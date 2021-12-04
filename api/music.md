## 获取【歌单列表】

> 通过该接口，你可以获取到全部的歌单数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/music</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| limit | 否 | int | 5 | 数据数量 |
| page | 否 | int | 1 | 分页请求 |
| order | 否 | string | create_time ase | 排序方式 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/music',
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
axios.get('http://test.inis.cn/api/music').then((res) => {
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
$url  = 'http://test.inis.cn/api/music';

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
                "title":"日语歌单",
                "description":"",
                "url":"https://c.y.qq.com/base/fcgi-bin/u?__=t4JqWm4x",
                "is_show":1,
                "expand":{
                    "type":"tencent"
                },
                "opt":null,
                "create_time":"2021-06-04 21:54:33",
                "update_time":"2021-06-04 23:21:04"
            },
            {
                "id":2,
                "title":"古风歌单",
                "description":null,
                "url":"https://c.y.qq.com/base/fcgi-bin/u?__=kcNQEm4v",
                "is_show":1,
                "expand":{
                    "type":"tencent"
                },
                "opt":null,
                "create_time":"2021-06-05 00:46:08",
                "update_time":"2021-06-05 00:46:08"
            }
        ]
    }
}
```
</details>




## 获取【单个歌单】数据

> 通过该接口，你可以获取歌单的信息，不包含歌单列表数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/music</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| id | 否 | string | 无 | 歌单ID |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/music',
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
axios.get('http://test.inis.cn/api/music',{
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
$url  = 'http://test.inis.cn/api/music?id=1';

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
        "id":1,
        "title":"日语歌单",
        "description":"",
        "url":"https://c.y.qq.com/base/fcgi-bin/u?__=t4JqWm4x",
        "is_show":1,
        "expand":{
            "type":"tencent"
        },
        "opt":null,
        "create_time":"2021-06-04 21:54:33",
        "update_time":"2021-06-04 23:21:04"
    }
}
```
</details>






## 获取【歌单内歌曲列表】

> 通过该接口，你可以获取歌单下的全部音乐列表数据，不包含播放地址，播放地址在下一个接口获取

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/music</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| id | 否 | string | 无 | 无 | 歌单ID | 无 |
| mode | 否 | string | 无 | list | 模式 | 无 |
| shuffle | 否 | bool | false | true、false | 是否随机 | 仅在关闭缓存的情况下生效 |
| cache | 否 | bool | true | true、false | 是否获取缓存数据 | 无 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/music',
  type:'GET',
  dataType:'JSON',
  data: {"id":1,"mode":"list"},
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
axios.get('http://test.inis.cn/api/music',{
    params:{ "id":1,"mode":"list" }
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
$url  = 'http://test.inis.cn/api/music?id=1&mode=list';

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
        "info":{
            "id":1,
            "title":"日语歌单",
            "description":"",
            "url":"https://c.y.qq.com/base/fcgi-bin/u?__=t4JqWm4x",
            "is_show":1,
            "expand":{
                "type":"tencent"
            },
            "opt":null,
            "create_time":"2021-06-04 21:54:33",
            "update_time":"2021-06-04 23:21:04"
        },
        "songs":[
            {
                "name":"Tokyo Bon 東京盆踊り2020",
                "url":"",
                "song_id":"003P4xng35mSgF",
                "cover":"https://y.gtimg.cn/music/photo_new/T002R300x300M000001ZaCQY2OxVMg.jpg?max_age=2592000",
                "author":"黄明志Namewee"
            },
            {
                "name":"HACK",
                "url":"",
                "song_id":"003spmCw03Q0yc",
                "cover":"https://y.gtimg.cn/music/photo_new/T002R300x300M000001pmbyO4JoXhB.jpg?max_age=2592000",
                "author":"末吉秀太"
            },
            {
                "name":"海底",
                "url":"",
                "song_id":"003kPENV3fUK9k",
                "cover":"https://y.gtimg.cn/music/photo_new/T002R300x300M000003W7doV14AWkE.jpg?max_age=2592000",
                "author":"黑崎子"
            },
            {
                "name":"绊",
                "url":"",
                "song_id":"001KJbqO3h7V8N",
                "cover":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000023S10X2rxpLj.jpg?max_age=2592000",
                "author":"Nightcore.Shiro"
            },
            {
                "name":"彼女は旅に出る",
                "url":"",
                "song_id":"000JCLKZ2XVZCr",
                "cover":"https://y.gtimg.cn/music/photo_new/T002R300x300M0000009lYKe4VidrF.jpg?max_age=2592000",
                "author":"鎖那"
            }
        ]
    }
}
```
</details>





## 获取歌曲【播放地址】数据

> 通过该接口，你可以获取指定歌曲的播放地址以及其他数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/music</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 | 备注 |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| id | 否 | string | 无 | 无 | 歌曲ID | 上一个接口返回的song_id |
| mode | 否 | string | 无 | song | 模式 | 无 |
| who | 否 | string | tencent | tencent、netease | 厂商 | 无 |
| cache | 否 | bool | true | true、false | 是否获取缓存数据 | 无 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/music',
  type:'GET',
  dataType:'JSON',
  data: {"id":"004D4uji2ceY5H","mode":"song","who":"tencent"},
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
axios.get('http://test.inis.cn/api/music',{
    params:{ "id":"004D4uji2ceY5H","mode":"song","who":"tencent" }
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
$url  = 'http://test.inis.cn/api/music?id=004D4uji2ceY5H&mode=song&who=tencent';

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
        "name":"字正腔圆",
        "url":"https://dl.stream.qqmusic.qq.com/M5000031MClk3P47aq.mp3?guid=126630400&amp;vkey=5E7332BD5BFEC8B115D466CAB7C2C0874944CFED9402E56326D7338CA906BA91230E2D1FC916D6C93B3E60057743BD95BE0843D3125F6A2D&amp;uin=&amp;fromtag=66",
        "song_id":"004D4uji2ceY5H",
        "cover":"https://y.gtimg.cn/music/photo_new/T002R300x300M000001zpUrT0JeP1G.jpg?max_age=2592000",
        "author":"伦桑"
    }
}
```
</details>
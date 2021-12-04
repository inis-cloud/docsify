## 通过【IP】获取地理位置

> 通过该接口，你可以获取地理位置   
> 支持IPV4和IPV6

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/location</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| ip | 否 | string | 客户端当前IP | 如果不提交，系统会自动获取 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/location',
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
axios.get('http://test.inis.cn/api/location').then((res) => {
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
$url  = 'http://test.inis.cn/api/location';

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
        "status":"1",
        "info":"OK",
        "infocode":"10000",
        "country":"中国",
        "province":"广西壮族自治区",
        "city":"贵港市",
        "district":"桂平市",
        "isp":"中国电信",
        "location":"110.074668,23.382473",
        "ip":"171.108.238.104"
    }
}
```
</details>




## 通过【经纬度】获取地理位置

> 通过该接口，你可以获取地理位置   

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/location/geocode</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| location | 否 | string | 客户端当前IP转换的经纬度 | 如果不提交，系统会自动获取 |
| cache | 否 | bool | true | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/location/geocode',
  type:'GET',
  dataType:'JSON',
  data: {"location":"110.074668,23.382473"},
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
axios.get('http://test.inis.cn/api/location/geocode',{
    params:{ "location":"110.074668,23.382473" }
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
$url  = 'http://test.inis.cn/api/location/geocode?location=110.074668,23.382473';

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
        "status":"1",
        "regeocode":{
            "addressComponent":{
                "city":"贵港市",
                "province":"广西壮族自治区",
                "adcode":"450881",
                "district":"桂平市",
                "towncode":"450881100000",
                "streetNumber":{
                    "number":"10号",
                    "location":"110.075137,23.382587",
                    "direction":"东",
                    "distance":"49.5057",
                    "street":"泰和街"
                },
                "country":"中国",
                "township":"西山镇",
                "businessAreas":[
                    [

                    ]
                ],
                "building":{
                    "name":[

                    ],
                    "type":[

                    ]
                },
                "neighborhood":{
                    "name":[

                    ],
                    "type":[

                    ]
                },
                "citycode":"1755"
            },
            "formatted_address":"广西壮族自治区贵港市桂平市西山镇泰和街10号"
        },
        "info":"OK",
        "infocode":"10000"
    }
}
```
</details>




## 获取【天气】信息

> 通过该接口，你可以获取指定友链的详细数据

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/location/weather</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 可选参数 | 说明 |
| :---- | :---- | :---- | :---- | :---- | :---- |
| adcode | 否 | string | 系统自动获取 | 无 | 如果不提，系统自动 |
| type | 否 | string | base | base、all | base=实况天气;all=预报天气 |
| cache | 否 | bool | true | true、false | 是否获取缓存数据 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
$.ajax({
  url:'http://test.inis.cn/api/location/weather',
  type:'GET',
  dataType:'JSON',
  data: {"adcode":450881},
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
axios.get('http://test.inis.cn/api/location/weather',{
    params:{ "adcode":450881 }
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
$url  = 'http://test.inis.cn/api/location/weather?adcode=450881';

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
        "status":"1",
        "count":"1",
        "info":"OK",
        "infocode":"10000",
        "lives":[
            {
                "province":"广西",
                "city":"桂平市",
                "adcode":"450881",
                "weather":"多云",
                "temperature":"32",
                "winddirection":"东北",
                "windpower":"≤3",
                "humidity":"54",
                "reporttime":"2021-08-28 15:32:55"
            }
        ]
    }
}
```
</details>



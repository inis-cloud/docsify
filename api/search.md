## 【关键词】搜文章

> 通过该接口，你可以根据关键词搜索站内的文章

<p class="api-request get" data-lang="API"><em></em>http://[域名]/api/search</p>

`请求参数：`**[有]**

| 参数名称 | 是否必选 | 参数类型 | 默认值 | 说明 |
| :---- | :---- | :---- | :---- | :---- |
| value | 是 | string | 无 | 搜索的内容 |
| sort_id | 否 | int | 无 | 文章分类ID |
| limit | 否 | int | 5 | 数据数量 |
| page | 否 | int | 1 | 分页请求 |
| order | 否 | string | create_time desc | 排序方式 |

<!-- tabs:start -->

#### ** ajax **

```html
<!-- 导入JQ -->
<script src="//code.jquery.com/jquery-3.5.1.min.js"></script>

<script>
// 搜索按钮
$('#btn-search').on('click', () => {
	
    let value      = 'inis';
    let sort_id	= 1;

    let data = {value,sort_id};

    $.ajax({
          url:'http://test.inis.cn/api/search',
          type:'GET',
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
axios.get('http://test.inis.cn/api/search',{
	params: {
		value    : 'inis',
		sort_id  : 1,
	}
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
$url  = 'http://test.inis.cn/api/search?value=inis&sort_id=1';

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
    "msg":"搜索成功！",
    "data":[
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
                    "Vue",
                    "ThinkPHP6"
                ],
                "author":{
                    "nikename":"兔子",
                    "head_img":"http://inis.racns.com/img/userHead.gif",
                    "email":"racns@qq.com",
                    "address_url":"https://inis.cn",
                    "description":"许一人以偏爱，尽此生之慷慨！"
                },
                "comments":9
            },
            "create_time":"2020-10-01 15:26:47",
            "update_time":"2020-12-18 13:23:01"
        },
		... ...
		{...},
		{...}
    ]
}
```
</details>
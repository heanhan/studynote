java中fastjson使用
===
###fastjson开始集成使用
	fastjson 添加pom坐标
```
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>fastjson</artifactId>
            <version>1.2.58</version>
        </dependency>
```
使用：
		1.Map转换为 JSON

```
Map<String,Object> map = new HashMap<>();
map.put("uername","zhaojh");
map.put("password","123456");
JSONObject json = new JSONObject(map);
```
		2.JSON 转换为String

```
JSONObject json = new JSONObject();
json.put("username","zhaojh");
json.put("password","123456");
json.toJSONString();//调用toJSONString()方法；
```
		3.JSON转换为Map

```
JSONObkect json = new JSONObject();
json.put("username","zhoajh");
json.put("password","123456");
Map<Stirng,Object> map = (Map<String,Object>)json;
```
		4.String转JSON

```
String str="{\"username\":\"zhoajh\",\"password\":\"123\"}";
JSONObject json= JSONObject.parseObject(str);
```


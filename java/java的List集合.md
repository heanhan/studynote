java的List集合
===

###  List 集合出去所有的null和""

```
方法一：
将List 集合  realList 去null和""
//临时集合
List<Object> templeList = new ArrayList<>();
for(int i= 0;i<realList .size;i++){
    //保存不为空的元素
    if(realList .get(i) !=null&&realList.get(i)!=""){
       templeList .add(realList .get(i));
  }
}


方法二： 使用系统集成的api

realList.removeNull(Collections.singleton(""));
realList.removeNull(Collections.singleton(null));
```


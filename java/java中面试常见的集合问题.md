说说List,Set,Map三者的区别？
   - List（对付顺序的好帮手）List集合存储一组不唯一（可以有多个元素引用相同的对象）,有序的对象
   - Set(注重独一无二的性质),不允许重复的集合，不会有多个元素引用相同的对象。
   - Map (用key来搜索的专家）使用键值对存储，map会维护与key有关联的值，两个key可以引用相同的对象，但key
   不能重复，典型的key是String 类型，但也可以是任何对象。
   
   
ArrayList 与LInkedList的区别？
- 是否保证线程安全：ArrayList和LinkedList都是线程不同步的，也就是不保证线程安全。
- 底层的数据结构：ArrayList 底层是使用Object数组，LinkedList是使用双向链表数据结构，
- 插入和删除是否受到元素的位置的影响：
## JSON 操作
---

**JSON.stringify()**, 将value(Object,Array,String,Number...)序列化为JSON字符串 

**JSON.parse()**,　将JSON数据解析为js原生值 

**toJSON()**, 作为JSON.stringify中第二个参数(函数过滤器)补充 

 执行原理： 

    /* 

     * toJSON() 作为JSON.stringify中第二个参数(函数过滤器)补充，理解内部顺序很重要。 

     * 假设把一个对象传入JSON.stringify() 序列化对象的顺序如下： 

     *  

     * (1) 如果存在toJSON()方法而且能通过它取得有效的值，则调用该方法。否则，按默认顺序执行序列化 

     * (2) 如果提供了第二个参数，应用这个函数过滤器，传入的函数过滤器的值是第(1)步返回的值。 

     * (3) 对第(2)步 返回的每个值进行相应的序列化。 

     * (4) 如果提供了第三个参数，执行相应的格式化操作。 

    */ 
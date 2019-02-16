## 节点操作
---

> ### 元素操作

**lastElementChild**  最后一个子节点 

**firstElementChild**  第一个子节点 

**nextElementSibling**  下一个兄弟节点 

**previousElementSibling** 上一个兄弟节点 

**parentNode**  父节点 

**children**    元素的子节点 

**childNode**   子节点 包括元素和文本 

**replaceChild()**  替换元素中的子节点 

**nodeType** 节点类型 

**attributes** 节点属性 

**createElement** 创建节点（元素） 

**removeChild** 删除子节点 

**appendChild** 添加子节点 

**insertBefore** 添加子节点(在谁的前面添加) 

**cloneNode** 克隆  

**getAttribute** 获取行间属性的值 

**setAttribute** 设置行间属性值 

**removeAttribute** 删除行间属性 



> ### 获取页面宽度、高度、位置

**offsetParent** 带有定位（position 不包括 static ）最近的父节点 

**offsetLeft** 节点的外边框到最近的带有定位的父级的内边框 

**offsetTop**  节点的外边框到最近的带有定位的父级的内边框 

**getBoundingClientRect**  获取元素节点的相对于可视区域的位置和宽高（宽高带边框） 

**document.documentElement.clientWidth** 可视宽度 

**document.documentElement.clientHeight** 可视高度 

**document.body.scrollTop** 在谷歌中使用获取滚动 

**document.documentElement.scrollTop** 火狐中使用 

*scroll = document.body.scrollTop || document.documentElement.scrollTop;*

 

**var target = ev.target || ev.srcElement;** //事件源的兼容处理 

**e.clientX** 鼠标X轴位置 

**e.clientY** 鼠标Y轴位置 

**currentStyle getComputedStyle**  获取最终样式 

**DOMContentLoaded** 等待DOM 加载完成后执行 
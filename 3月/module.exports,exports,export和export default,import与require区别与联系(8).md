### module.exports、exports、export和export default，import和require区别与联系！

一、首先搞清楚一个基本问题：

module.exports和exports是属于 _CommonJS_ 模块规范！（不清楚commonjs?大神请这边逛一逛commonjs规范）

export和export default是属于 _ES6_ 语法（不清楚ES6?大神请这边逛一逛ES6模块）！

同样import和require分别属于ES6和CommonJS！

二、知道属于哪一块的语法了还有一个明确点：

module.exports和exports、export和export default都是导出模块；

import和require则是导入模块。

所以现在就不要弄混了，module.exports导出对应require导入，export导出对应import导入。

喂！等等，怎么才说到module.exports导出对应require导入，export导出对应import导入，那还有exports和export default呢！？那我们继续。

三、module.exports和exports的区别与联系

讲到这里就不得不稍微提一下模块化：

Node应用由模块组成，采用CommonJS模块规范。

 

根据这个规范，每个文件就是一个模块，有自己的作用域。在一个文件里面定义的变量、函数、类，都是私有的，对其他文件不可见。

CommonJS规范规定，每个模块内部，module变量代表当前模块。这个变量是一个对象，它的exports属性（即module.exports）是对外的接口。加载某个模块，其实是加载该模块的module.exports属性。

```
var x = 5;
var addX = function (value) {
  return value + x;
};
module.exports.x = x;
module.exports.addX = addX;
```


上面代码通过module.exports输出变量x和函数addX。

require方法用于加载模块。

```
var example = require('./example.js');

console.log(example.x); // 5
console.log(example.addX(1)); // 6
```
 

看了刚刚这段commonjs规范上面的介绍可以知道以下区别与联系：

 

其实exports变量是指向module.exports，加载模块实际是加载该模块的module.exports。这等同在每个模块头部，有一行这样的命令。

 
```
var exports = module.exports;
```
 

于是我们可以直接在 exports 对象上添加方法，表示对外输出的接口，如同在module.exports上添加一样。注意，不能直接将exports变量指向一个值，因为这样等于切断了exports与module.exports的联系。

三、export和export default的区别与联系

模块功能主要由：export和import构成。export导出模块的对外接口，import命令导入其他模块暴露的接口。

export其实和export default就是写法上面有点差别，一个是导出一个个单独接口，一个是默认导出一个整体接口。使用import命令的时候，用户需要知道所要加载的变量名或函数名，否则无法加载。这里就有一个简单写法不用去知道有哪些具体的暴露接口名，就用export default命令，为模块指定默认输出。

export可以这样写

```
// testA.js
var f = 'Miel';
var name = 'Jack';
var data= 1988;

export {f, name, data};
```

使用export命令定义了模块的对外接口以后，其他 JS 文件就可以通过import命令加载这个模块。

```
// main.js
import {
f, name, data
} from './testA';

export default可以这样写

// export-default.js
export default function () {
  console.log('foo');
}

// 或者写成

function foo() {
  console.log('foo');
}
export default foo;

// import-default.js
import customName from './export-default';
customName(); // 'foo'
```
下面比较一下export default和export 输出。

```
// 第一组
export default function car() { // 输出
  // ...
}

import car from 'car'; // 输入

// 第二组
export function car2() { // 输出
  // ...
};

import {car2} from 'car2'; // 输入
```

可以看到第一组是使用export default，import 语句不需要使用大括号；第二组使用export，对应的 import语句需要使用大括号，一个模块只能有一个默认输出，所以 export default 只能使用一次。

四、import和require的区别与联系

看了上面其实已经清楚了，import和require是分别属于ES6和CommonJS的两种导入模块的语法而已。
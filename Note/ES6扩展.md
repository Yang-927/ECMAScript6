### 字符串扩展

1. 模板字符串

	##### 用单引号或者双引号定义字符串的缺点：

	1. 不可以换行
	2. 大量拼接时麻烦，还容易出错

	##### ES6用一对反引号定义字符串：

	1. 随意换行

	2. 不需要做字符串拼接工作，直接在字符串中嵌入变量

		**嵌入**

		```js
		${变量名|调用函数|运算}
		```

		**直接嵌入变量**

		```js
		
		```

		**运算**

		```js
		let age = 20;
		let str = `Curry今年${age > 18 ? 成年 : 未成年;}`;
		console.log(str);
		```

		**调用函数**

		```js
		let name = 'durant';
		function capitalize(str){
		    return str.charAt(0).toUpperCase() + str.slice(1).toLowerCase();
		}
		let str = `我是${capitalize(name)}`;
		console.log(str);
		```

2. 字符串几个方法

	includes：检测一个字符串是否包含另一个字符串，存在返回true，不存在返回false；

	```js
	let str = 'happy new year，新年快乐！'
	console.log(str.includes('year'));
	```

	startsWith：检测一个字符串是否以某个字符串开头；

	startsWith(str,[index]);不传index表示从0开始。

	```js
	let str1 = 'https://www.baidu.com';
	console.log(str1.startsWith('https',1));
	```

	endsWith：

	endsWith(str,[index = str.length - 1]);

	```js
	
	```

	

	repeat：把字符串重复指定次数拼接起来
	
	str.repeat(n)
	
	```js
	let str3 = 'China';
	console.log(str3.repeat(3));	// ChinaChinaChina
	```



### 数值的扩展

parseInt()，parseFloat()，isNaN()，这几个方法在ES5中都是window对象的方法，ES6中这几个方法不再属于window对象，而是属于Number的方法，如果使用ES6的方式来使用这几个方法，需要写成Number.XXX;

只是写法改变了，功能不变。



- Number.isFinite：检测一个数是不是有限的；

	```js
	console.log(Number.isFinite(-3));
	console.log(Number.isFinite(Math.PI));
	console.log(Number.isFinite(Infinity));
	console.log(Number.isFinite(2/3));
	console.log(Number.isFinite(-3));
	```

- Number.isInteger：检测一个数是否为整数，如果是返回true，否则返回false;

	```js
	console.log(Number.isInteger(-3));	// ture
	console.log(Number.isInteger(1.1));	// false
	console.log(Number.isInteger(2.0));	// true
	```



### Math扩展

Math.trunc：

​	取得一个小数的整数部分

```js
console.log(Math.trunc(4.3));	// 4
console.log(Math.trunc(0));		// 0
console.log(Math.trunc(-0));	// -0
console.log(Math.trunc(4));		// 4
```

Math.sqrt：

​	求平方根

Math.cbrt：

​	求得立方根

```js
console.log(Math.cbrt(27));	// 3
console.log(Math.cbrt(64));	// 4
```

Math.hypot：

​	求得和的平方根

```js
console.log(Math.hypot(6,8));	// 10
console.log(Math.hypot(3,4));	// 5
```

Math.pow()：

​	求幂运算；

**：

​	指数运算符

```js
console.log(2 ** 3);		// 2^3 = 8	Math.pow(2,3)	2 * 2 * 2
console.log(Math.pow(2,3));	// 2^3 = 8	2 ** 3			2 * 2 * 2
console.log(2 ** 0)			// 1
```

### 函数扩展

1. 函数参数的扩展

	1. 参数的默认值

	2. 可变参数

		函数在调用的时候，参数的个数不确定时，这时候函数形参写成可变参数的形式，例如

		```js
		function add(...args){
		    console.log(args)
		}
		add(1,2);		// [1,2]
		add(1,2,3);		// [1,2,3]
		
		function add(...args){
		    console.log(...args)
		}
		add(1,2);		// 1 2
		add(1,2,3);		// 1 2 3
		
		function add1(x,...args){
		    console.log(args)
		}
		add1(1,2);		// [2]
		add1(1,2,3);	// [2,3]
		
		function getMaxAndMin(...args){
		    return {
		        Max:Math.max(...args)
		        Min:Math.min(...args)
			}
		}
		console.log(getMaxAndMin(56,23,43,53,61,5,2,1,23,112));
		```

		**剩余参数必须作为最后一个形参，它的位置必须放在最后，否则会发生报错！**

2. 函数类型的扩展

	1. 箭头函数

	  定义：

	  ```js
	  // ES5普通函数
	  let fn = function(){
	      
	  }
	  // ES6箭头函数
	  let fn = () => {
	      
	  }
	  ```

	  特性：

	  1. 当函数只有一个形式参数时，可以省略小括号；

	  	```js
	  	let tol = a => {
	  		alert(a)
	  	}
	  	tol('Curry')
	  	```

	  2. 当函数体只有一句话时，可以省略大括号；

	  	```js
	  	let bar = (x,y) => alert(x ** y);
	  	
	  	bar(3,2)
	  	```

	  3. 当函数省略大括号后，函数自带return的功能；

	  	```js
	  	let pow = (x,y) => {
	  	    return x ** y
	  	}
	  	console.log(pow(2,4))
	  	
	  	let pow = (x,y) => x ** y;
	  	console.log(pow(2,4))
	  	```

	  4. 箭头函数不能通过new调用

	  5. 箭头函数没有arguments函数；

		```js
		let fn1 = () => {
		    console.log(arguments)	// 报错
		}
		fn1()
		```

		

	  6. **箭头函数内部this指向父级函数中this，箭头函数本身没有this指向问题；**

	  	this是一个关键字，this只能出现在函数中，代指一个对象，并且代指的这个对象会随着函数执行的环境（函数的调用方式）的不同随时发生变化，this指向哪个对象取决于谁在调用函数，谁调用就指向谁；
	
	```js
	function fn(){
	    console.log(this);
	}
	window.fn();	// window
	
	let obj = {
	    fn:function(){
	        console.log(this);
	    }
	}
	obj.fn();	// obj
	
	let oBtn = document.getElementById('btn');
	oBtn.onclick = function(){
	    console.log(this);	// oBtn
	}
	```
	
	​		**应用场景：**
	
	​			1. 
	
	2. 生成器函数
	
	3. 异步函数

### 数组的扩展

**新增方法**

forEach：遍历循环数组，类似for循环

```javascript
let arr = [1,2,3,4,5,6,7]
for(let i = 0; i < arr.length; i++){
    console.log(arr[i]);
}
for(let i in arr){
    console.log(arr[i])
}
arr.forEach(function(v,index){
    console.log(v,index)
})
```

map：映射，一一对应，由一个数组得到另一个数组，新数组中的每一项是由原数组中的每一项对应来的。

```javascript
let score = [58,64,43,78,60,32,98,59,61];
let result = score.map((v,index) => {
    console.log(v,index)
    if (v >= 60){
        return "及格"
    }else{
        return "不及格"
    }
})
console.log(result)
```

filter：

```js
let score = [56,78,60,48,32,99,12];
let result = score.filter(v => v % 2 ==0);
console.log(result);
```

find：

```js
let arr = [
    {
        id:1,
        name: 'YANG',
        age: 18
    },{
        id:2,
        name: 'Bin',
        age: 18
    },{
        id:3,
        name: 'Curry',
        age: 32
    },{
        id:4,
        name: 'Durant',
        age: 36
    },{
        id:5,
        name: 'FENG',
        age: 3
    }
]

let result = arr.find(item => item.id == 2);
console.log(result);
```

findIndex：

```javascript
let result = arr.find(item => item.id == 2);
console.log(result);
```

some：查找数组中是否有满足条件的元素，如果有，返回true，否则返回false；

```js
// 检测数组中是否有满足条件的元素
let result = arr.some(item => item.age === 18);
console.log(result);
```

every：检测数组中的元素是否都满足条件，如果满足，返回true，否则返回false；

```js
// 检测数组中的元素是否都满足条件
let result = arr.every(item => item.age == 18);
console.log(result);
```

fill：填充数组

```js
const arr = [11,22,33,44,55]

const res = new Array(100).fill(100,2);
console.log(res);

// 全部填充
// let ret = arr.fill(66);
// console.log(ret)

// 从指定位置开始填充
let ret = arr.fill(66,3)
console.log(ret)
```

flat：扁平化数组，括号里的值表示剥几层，不传参表示只剥一层，还可以传入Infinity（无穷）

```js
let arr = [2,[1,2,3],[6,3],[9,8,7]];
// 扁平化操作
let result = arr.flat()
console.log(result);	// [2, 1, 2, 3, 6, 3, 9, 8, 7]

let arr = [2,[1,2,[3]],[6,3],[9,8,7]];
// 扁平化操作
let result = arr.flat()
console.log(result);	// [2, 1, 2, Array(1), 6, 3, 9, 8, 7]
```

flatMap：先扁平，后映射

reduce：汇总

**有两种方法：**

1. array.reduce(function(current,next,index){})

	```js
	let arr = [1,2,3,4];
	le t sum = arr.reduce((current,next) => current + next);
	console.log(sum);
	```

2. ```js
	// 总价 
	let total = GOODS.reduce((init,next) => {
	  return init + next.unit * next.count;
	},0);
	// 总数量
	let num = GOODS.reduce((init,next)=> {
	  return init + next.count;
	},0)
	console.log(`total = ${total},num = ${num}`);
	```


includes：检测数组中是否存在某项，存在返回true，不存在返回false；

```js
let array = [11,22,33,44];
console.log(array.includes(24));
```

**数组的静态方法：**

Array.from：把一个伪（类/假）数组转换成一个真数组；

```js
<body>
	<div class="yang">1</div>
	<div class="yang">2</div>
	<div class="yang">3</div>
	<div class="yang">4</div>
	<div class="yang">5</div>
</body>
<script>
	let divs = document.getElementsByClassName('yang');
	console.log(divs);
	console.log(Array.from(divs))
	Array.from(divs).forEach(div => {
		console.log(div.innerHTML)
	})
</script>
```

Arrar.of：把一组值转换为数组；

```js
console.log(Array.of(1,2,3,4,5)); // [1, 2, 3, 4, 5];
```



### 对象的扩展：

1. 简写：

	```js
	let name = 'Durant';
	let obj = {
	    name,	// 等同于{name: name}
	    age: 32,
	    study(){
	        console.log(`${this.name},${this.age}`)
	    }
	    // 等同于{study: function(){}}
	}
	console.log(obj);
	obj.study();
	```

	特点：

	1. 当k和v名字一样是，只写一个；
	2. 存在方法是(:function)这些省略；

2. 对象新增静态方法

	1. Object.is()

		```js
		console.log(Object.is(1,'1'));	// false
		console.log(Object.is(1,1));	// true
		console.log(Object.is([],[]))	// false
		console.log(Object.is(NaN,NaN))	// true
		console.log(NaN === NaN)		// false
		```

	2. Object.assign()

		对象合并，把源对象和新的需要合并的对象一起合并

		```js
		let obj1 = {a: 1,b: 2};
		let obj2 = {c: 3,d: 4};
		let obj3 = {e: 5,f: 6};
		
		let ret = Object.assign(obj1,obj2,obj3);
		
		// obj === ret
		
		```

		assign只可以实现浅拷贝，不能实现深拷贝；

	3. Object.keys(obj);

		获取对象中的key值

		```js
		let obj = {x: 1,y: 2,z: 3};
		console.log(Object.keys(obj));	// ["x", "y", "z"];
		```

	4. Object.values(obj);

		获取对象中的value值

		```js
		let obj = {x: 1,y: 2,z: 3};
		console.log(Object.values(obj));// [1, 2, 3];
		```

	5. Object.entries：

		把对象所有的键以数组的形式返回；

		```js
		let obj = {x: 1,y: 2,z: 3};
		console.log(Object.entries(obj))
		```

3. 解构赋值

	1. 赋值符左右两边的结构必须一样；

	2. 赋值符号右边必须是个合法的数据类型；

		```js
		let {a,b,c} = {1,2,3}
		```

	3. 声明和赋值必须在同一句话内完成；

		```js
		let [a,b,c];
		[a,b,c] = array;
		```

4. 扩展运算符（...）：

	1. 可以实现解构赋值；

		```js
		let [a,...list] = [55,44,33,22];
		console.log(a,list);	// 55 (3) [44, 33, 22]
		```

	2. 可以实现数组或对象的复制；（一个改变另一个不会跟着改变）；

	  浅复制：改变一组的属性，另一组的属性不发生变化；

	  深复制：改变一组的属性另一组的属性相应随之变化；

	  ```js
	  let array = [55,44,33,22];
	  let arr2 = [...array]
	  console.log(arr2);	// [55, 44, 33, 22]
	  arr2.push(11);
	  console.log(arr2);	// [55, 44, 33, 22, 11]
	  console.log(array);	// [55, 44, 33, 22]
	  ```

	  ```js
    let obj1 = {a:1,b:3};
	  let obj2 = {...obj1}
	  console.log(obj2);
	  ```

	  
	
	3. 将一个假数组转化成一个真数组；
	
		```js
		
		```
	
	4. 将字符串转换成数组；
	
		```js
		let s = 'Hello World';
		[...s].forEach(c => {
		    console.log(c.charCodeAt())
		})
		```
	
		
	
	5. 合并数组或者对象
	
		```js
		// 合并数组
		let array1 = [1,2,3,4];
		let array2 = [5,6,7,8];
		let array3 = [...array1,...array2];
		console.log(array3)
		```
	
		```js
		// 合并对象
		let obj3 = {a:1,b:2};
		let obj4 = {c:3,d:4,e:5};
		let obj5 = {...obj3,...obj4};
		console.log(obj5)
		```
	
5. 属性值用变量；

	用中括号把变量包起来，今后这个属性名就会被变量替换；

	```js
	let x = 'address';
	let obj = {
	    name: 'Curry',
	    [x]: "中国林州"
	}
	console.log(obj);	// 
	```




### Symbol数据类型

symbol：ES6新增的一中数据类型，创建后就是独一无二的；

创建symbol数据类型，需要通过Symbol函数；

```js
let s = Symbol();
console.log(typeof s);	// symbol
console.log(s);			// Symbol()
```

**特点：**

1. 通过Symbol函数生成symbol数据，就是独一无二的，与其他数据都不等；

2. 不可以参与运算；

3. true真； 

	```js
	console.log(Boolean(s));	// true
	```

**关于Symbol函数传参问题：**

为了让创建出来的Symbol对象能够直观的看出其含义，有时候会在Symbol()方法执行的时候传入一个字符串参数，但创建出来的Symbol对象特性不变；

```js
let s = Symbol('说明信息');
```



**静态方法：**

Symbol.for('说明信息的字符串')：根据传入的key生成一个Symbol对象，不过在创建之前，他会想去全局检测是否存在这个key对应的Symbol对象；

```js
let s1 = Symbol('说明信息');
let s2 = Symbol('说明信息');

console.log(s1 === s2);		// true
```

**应用：**

作为对象的key，对象的key不可以重复，而通过Symbol创建的对象恰恰是独一无二的；

当一些对象的默认属性不想被访问，那么就将属性创建为Symbol类型；

```js
let obj = {
    [Symbol('a')]: 1,
    [Symbol('a')]: 2
}
console.log(obj);	// {Symbol(a): 1, Symbol(a): 2}
```

如果对象key是symbol类型，是不能被for-in循环遍历的；



### 迭代器：

迭代就是循环；

```js
let arr = [1,2,3,4,5];
for (var i = 0; i < arr.length; i++) {
    console.log(arr[i]);
}
```

迭代：执行和for循环类型，支部过普通for循环是通过下标取值的，迭代是通过指针

**如何检测一个对象是否可以迭代：**

​	访问该对象的Symbol.iterator属性，如果结果是一个函数，表名该对象可以迭代，否则不可迭代；

**如何获取可迭代对象的元素：**

1. 获取迭代器的对象：

	```js
	let iter = obj[Symbol.iterator];
	```

2. 通过调用迭代器对象next方法：

	第一次调用next方法，访问的是可迭代对象的第一个元素
	第一次调用next方法，访问的是可迭代对象的第一个元素
	以此类推

	每次next返回的是一个对象，该对象包含两个属性，一个是value，一个是done；value表示此次迭代取出的元素，done表示这个对象是否迭代完成，没有完成done值为false，否则为true；

	```javascript
	let arr1 = [1,2];
	console.log(arr[Symbol.iterator])
	let iter = arr1[Symbol.iterator]();
	if(iter){
	    // 开始迭代。index = 0 ;
	    console.log(iter.next());	// arr1[0]
	    console.log(iter.next());	// arr1[1]
	    console.log(iter.next());	// arr1[2]
	    console.log(iter.next());	// arr1[3]
	}
	```

**原理：**

```js
let iter1 = arr[Symbol.iterator]();
while(true){
    let {value,done} = iter1.next();
    if(!done){
        console.log(value);
    }else{
        break;
    }
}
```

**ES6新增：**

ES6新增for...of循环

```js
let arr = [1,2,3,4,5,6,7];
for(let item of arr){
    console.log(item);
}

let str = "Curry";
console.log(str[Symbol.iterator]);
for(let item of str){
    console.log(item);
}
```

**for...of遍历节点集合：**

```js
let liList = document.getElementsByTagName('li');
console.log(liList[Symbol.iterator])
for(let item of liList){
	item.style.color = '#f00';
}
```

**对象不可迭代：**

```js
const obj = {
    name: 'YangBinran',
    age: 18,
    sex: 'male'
}
console.log(obj[Symbol.iterator]);	// undefined
```

**for...of遍历arguments**

```js
function fn(){
    for(let item of arguments){
        console.log(item);		// a b c d e f g
    }
}
fn('a','b','c','d','e','f','g');
```



**for...of循环：**

1. 为所有可迭代对象提供一个统一的遍历手段
2. 与下标没有关系
3. 本质就是在调用next函数






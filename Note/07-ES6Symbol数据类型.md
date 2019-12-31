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
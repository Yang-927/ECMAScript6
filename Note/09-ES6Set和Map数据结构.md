## Set和Map数据结构

### Set：

**概念：**

​	集合，存储一组唯一的，无序的数据的容器

**创建：**

```js
let set = new Set();
console.log(set);
```



**特点：**

1. 唯一性

	```js
	let set new Set([1,2,1,1,3,4,2,5,4,5,2,3]);
	console.log(set);	// [1,2,3,4,5]
	```

2. 无序性

	```js
	console.log(set[0]);	// undefined
	console.log(set[1]);	// undefined
	console.log(set[2]);	// undefined
	```

**使用Set对数组快速去重：**

```js
let arr = [1,2,3,4,51,2,3,5,1,4,1,2,3,4,5,5,2];
console.log([...new Set(arr)]);
```

**属性：**

1. size：集合中元素的个数，跟数组的length属性一样

	```js
	let set = new Set('Curry');
	console.log(set.size);	// 4
	```

	

**方法：**

1. add('str')：添加
2. delete('str')：删除
3. has('str')：查询，是否含有
4. clear()：清空集合
5. forEach()：遍历集合
6. keys()：
7. values()：
8. entries：

**注意：**

1. 集合中元素不能获取，也不可以修改；

2. 集合可以被for...of遍历；

	```js
	console.log(set[Symbol,iterator]);
	for(let item of set){
	    console.log(item);
	}
	```

3. set结构的键名和键值是同一个值
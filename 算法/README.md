1.数组去重

>使用ES6的Set去重, Set是ES6新增的数据类型，Set 的成员具有唯一性
```
function distinct(arr) {
  return Array.from(new Set(arr));
}
```

>使用ES6的Set去重(超级简化版)

`[...new Set(arr)]   // [...new Set(需要去重的数组)]`

使用splice配合两重for循环去重

```
function distinct(arr) {
  for(let i = 0; i < arr.length; i++) {
  	for(let j = i + 1; j < arr.length; j++) {
  		if(arr[i] === arr[j]) {
  			arr.splice(j, 1);
  			j--;
  		}
  	}
  }
  return arr;
}
```

>使用for循环配合indexOf去重
```
 function distinct(arr) {
 	let newArr = [];
 	for(let i = 0; i < arr.length; i++) {
 		if(newArr.indexOf(arr[i]) === -1) {
 			newArr.push(arr[i]);
 		}
 	}
 	return newArr;
}
```

>使用for循环配合sort排序去重

```
function distinct(arr) {
  	arr = arr.sort();
  	let newArr = [];
  	for(let i = 0; i < arr.length; i++) {
  		if(arr[i] !== arr[i-1]) {
      		newArr.push(arr[i]);
  		}
  	}
  	return newArr;
  }
```

>使用for循环配合includes去重
```
  function distinct(arr) {
  	let newArr = [];
  	for(let i = 0; i < arr.length; i++) {
  		if(!newArr.includes(arr[i])) {
  			newArr.push(arr[i]);
  		}
  	}
  	return newArr;
 }
```

>使用filter配合indexOf去重
```
function distinct(arr) {
  	return arr.filter((item,index, arr) => arr.indexOf(item) === index);
}
```

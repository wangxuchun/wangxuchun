**gitHub:**

账号:wxc021   密码:wangxuchun5418

账号:875770925 密码:duoluo_021!

***ES8   新增的操作对象的属性***

```js
let obj = {name:'嘻哈小C',age:'26'};

Object.values(obj);	//['嘻哈小C','24'];

Object.keys(obj);	//['name','age'];

Object.entries(obj);//[['name','嘻哈小C'] , ['age','24'] ]  对象转化为二维数组
//copy 对象的方式
let obj1 = {name:'王叙淳',age:'26',nickname:'嘻哈小C'};
let obj2 = {name:'王叙淳',age:'26',nickname:'嘻哈CC',id:'1314'};

//进行数组的copy
let arr1 = [1,2,3];
let arr2 = [4,5,6];
arr1.push(...arr2);//arr1 = [1,2,3,4,5,6];





```


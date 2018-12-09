数组的扁平化(3种方法)：
1.function myFlat ( arr ){
	return [].concat(...arr.map( x => Array.isArray(x) ? myFlat( x ) : x));
}
2.
function myFlat ( arr , res ){
	res == udefined ? res = [] : res;
	arr.forEach( e => Array.isArray(e) ? myFlat( e, res) : res.push( e ));
	return res;
}
myFlat([1,2,3,[4,32,21]]);
注意点;
1.不会多次返回结果，因为是forEach完之后才会return，只会执行一次return 
2.在第二次执行myFlat( e,res ),这里的形参是上面执行后的值，即[4,32,21] 和[1,2,3]
3.像上面执行，是不会打印出东西的，只是有返回值，当let aa = myFlat([1,2,3,[4,32,21]]);   
console.log(aa) 才会打印出东西;或者console.log(myFlat([1,2,3,[4,32,21]]);)

3.
function myFlat(arr, result) {
            if (!result) {
                var result = []
            }
            for (var i = 0; i < arr.length; i++) {
                var cur = arr[i];
                if (typeof cur === 'object') {
                    myFlat(cur, result);
                } else {
                    result.push(cur)
                }
            }
            return result;
        }




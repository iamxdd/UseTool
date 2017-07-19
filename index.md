/**
 * 限制数字且最多输入小数的位数
 * @param  {[type]} elem 输入的对象
 * @param  {[type]} len  输入长度
 * @return {[type]}      [description]
 */
function limitNumber(elem, len) {
	elem.addEventListener("input",function(e){
		var result = "";
		var val = e.target.value;
		//最后一个字符是.
		if (val[val.length - 1] === ".") {
			//如果.符号超过一个
			if (val.split(".").length > 2) {
				val = val.slice(0, -1);
			} else if (val.split(".").length === 2 && val.slice(val.indexOf("."), val.length - 1).length > 2) {
				val = val.slice(0, val.indexOf(".") + 2)
			}
		}
		//存在.符号并且不止一位数
		else if (val[val.length - 1] !== "." && val.indexOf(".") !== -1) {
			val = val.slice(0, val.indexOf(".") + (len || 2 + 1))
		}
		e.target.value = val.replace(/[^\d\.]/g, "");
	})
}

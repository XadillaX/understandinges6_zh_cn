# 迭代器和生成器


## 语句


### for-of

在ECMAScript5以及之前的版本，如果你需要迭代一个数组中的值，你需要几个选项。当然了，你可以使用可靠的 `for` 循环：

    var i, len;

    for (i=0, len=values.length; i < len; i++) {
        process(values[i]);
    }

你也可以使用 `forEach()` 方法：

    values.forEach(function(value) {
        process(value);
    });

然而, 这些方法都有一些局限性。 `for` 循环需要以变量的形式进行一些设置；  `forEach()`只适用于数组而不适用于类数组对象。ECMAScript 6为解决这些问题提供了一个新的语句。 

`for-of` 语句被设计用于迭代任何类数组对象里的值。你不需要设置一个变量用来监测项在数组中的进程，你只需要简单的使用一个变量来分配数组中的每个后续的值，直到所有的值都通过循环。例如：

    for (let value of values) {
        process(value);
    }

在这段代码中， `for-of` 循环限定使用变量 `value` 来保存在数组 `values` 中的每个值。这个循环开始于数组中的第一个值，然后顺序移动通过这个数组直到数组结束。因为这个语句可以使用于任何类数组对象，所以你可以用在 `arguments` 和 DOM `NodeList` 对象上（这两者都没有 `forEach()` 方法）：

    // 输出所有参数
    function printArgs() {
        for (let arg of arguments) {
            console.log(arg);
        }
    }

    // 迭代所有 <div> 元素
    var divs = document.getElementsByTagName("div");

    for (let div of divs) {
        div.innerHTML = "Processed...";
    }


比起那些必须考虑不同对象类型的迭代方法，适用于任何类数组对象的 `for-of` 方法的性能有着巨大的提升。

笔记： `for-of` 语句可以用于任何可迭代的对象，包括数组，arguments, DOM `NodeList` 对象和Generators对象。但是它不适用于正则对象。

对于字符串来说， `for-of` 迭代器会遍历其码点。



#### @@迭代器


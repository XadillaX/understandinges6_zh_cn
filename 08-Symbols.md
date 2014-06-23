# 符号 (Symbols)

> 本章还在实施中。所以比其它章节会有更多的错别字或者内容错误。

ECMAScript 6 中符号开始作为一种创建私有对象成员的方式——一个 JavaScript 程序员所梦寐以求的特性。它着重于创建那些不是由字符串命名的属性。任何拥有字符串标识符的属性都是可以被轻而易举被外界访问到，即使它的名字破破烂烂的。最初的“私有名 (Private Names)”功能就是创建属性的非字符串名字。如此一搞，正常的科技（黑科技除外）是无法侦测到这些私有名的。

值得高兴的是，私有名的建议最终被采纳然后在 ECMAScript 6 中变成了符号 (Symbols)。它的细则实施仍然保持不变（属性标识符为一个非字符串的值），TC-39 放弃了这些属性要变成私有的需求——这些属性转而将会被另外分类，仍可被发现但是默认情况下不可被枚举。

符号 (Symbols) 实际上是一种新的基本值，加入字符串、数字、布尔类型、`null` 以及 `undefined`。它们在 JavaScript 基本类型中很特殊，因为他们没有文字形式。在 ECMAScript 6 标准中使用了一种特殊的形式来表示符号——使用 `@@` 作为标识符的前缀，如 `@@create`。为了便于理解，本书使用相同的约定。

> 尽管有前缀，符号并不确切映射到以 `@@` 开头的字符串。你不要妄想着在需要用符号的时候使用字符串的值来替代。

## 创建符号

你可以通过 `Symbol` 函数来创建一个符号，如：

```javascript
var firstName = Symbol();
var person = {};

person[firstName] = "Nicholas";
console.log(person[firstName]);     // "Nicholas"
```

在样例中，一个叫 `firstName` 的符号被创建了，而且这小家伙被用来给 `person` 分贝了一个新的属性。当你每次想要访问这个属性的时候，你必须使用这个符号。不过为了你的性福生活着想，我们建议给符号取一个恰当好听的名字——不要使用一些无意义的单词什么的。

> 因为符号是一种基本值，`new Symbol()` 就会抛出错误。别想尝试着去实例化一个 `Symbol`，因为它跟所谓的 `String`、`Number` 以及 `Boolean` 根本不是一路人。

`Symbol` 函数有一个可选参数，你可以用它来描述这个符号。当然这个描述本身不能用于访问属性，它仅仅是用于调试用的。举个栗子说：

```javascript
var firstName = Symbol("first name");
var person = {};

person[firstName] = "Nicholas";

console.log("first name" in person);    // false
console.log(person[firstName]);         // "Nicholas"
console.log(firstName);                 // "Symbol(first name)"
```

符号的描述被储存在内部叫 `[[Description]]` 的属性当中。无论每当显示或者隐式地使用符号的 `toString()` 函数时，这个属性就会被读取（就跟上面的栗子里面说的一样）。除此之外，你想直接访问 `[[Description]]` 别无他法。无论是用于静态阅读代码或者调试代码，我们推荐都为符号提供一个描述，这样就可以跟代码更愉快地玩耍了。

## 检测符号类型

是的是的没错，符号是基本值，所以你可以用 `typeof` 来检测其类型。ECMAScript 6 为 `typeof` 做了扩展——当后面跟着一个符号的时候会返回 `"symbol"`。例如：

```javascript
var symbol = Symbol("test symbol");
console.log(typeof symbol);         // "symbol"
```

虽然呢用别的间接方法来确定符号这种类型也不是不可以，但是 `typeof` 这种运算是最精确也是首选方案呢。

## 使用符号

你可以在任何你需要用已经搞好的属性名的时候使用符号。相信前面章节中使用括号的形式已经亮瞎了你们的氪金狗眼。但是！你可以在运算出来的对象字面属性名中使用符号，用 `Object.defineProperty()` 以及 `Object.defineProperties()`。例如：

```javascript
var firstName = Symbol("first name");
var person = {
    [firstName]     : "Nicholas"
};

// make the property read only
Object.defineProperty(person, firstName, { writable: false });

var lastName = Symbol("last name");
Object.defineProperties(person, {
    [lastName]  : {
        value: "Zakas",
        writable: false
    }
});

console.log(person[firstName]);     // "Nicholas"
console.log(person[lastName]);      // "Zakas"
```

对于对象字面形式中已计算的属性名，符号非常容易使用。*

## 共享符号

TODO

## 找到对象符号

TODO

## 广知符号

TODO

### @@toStringTag

TODO

### @@toPrimitive

TODO

### @@isConcatSpreadable

TODO

### @@unscopeables

TODO

### @@isRegExp

TODO

### @@iterator

TODO

### @@create

TODO

### @@hasInstance

TODO

## 摘要

TODO

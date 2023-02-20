# regexprefer

regexprefer 是一个备忘录，帮助你找到最适合字符串的正则表达式。

## 锚点

* `^` 字符串的开始，或者配合 `[]` 使用，表示非某个字符
* `$` 字符串的结束
* `b` 单词边界
* `B` 非单词边界

## 模式

* `i` 忽略大小写
* `m` 多行
* `g` 全局

## 字符类

* `[abc]` 字符集 
* `[^abc]` 非 a 或 b 或 c 的字符
* `[a-z]` 范围 
* `.` 任意字符
* `\w` 单词
* `\W` 非单词
* `\d` 数字
* `\D` 非数字
* `\s` 空白字符
* `\S` 非空白字符

## 组

* `()` 分组
* `\1` 引用第一个分组
* `(?:)` 非捕获分组

## 预查

<b><details><summary>`(?=)` 正向预查</summary></b>
```js
const str = '1st 2nd 3rd'
const reg = /\d(?=nd)/g // 2
```
</details>

<b><details><summary>`(?!)` 负向预查</summary></b>
```js
const str = '1st 2nd 3rd'
const reg = /\d(?!nd)/g // 1 3 
```
</details>

<b><details><summary>`(?<=)` 正向往前预查</summary></b>
```js
const str = '#1 $5 %8'
const reg = /(?<=%)\d/g // 8 
```
</details>

<b><details><summary>`(?<!)` 负向往前预查</summary></b>
```js
const str = '#1 $5 %8'
const reg = /(?<!%)\d/g // 1 5 
```
</details>


<b><details><summary>`?` 总结</summary></b>
`?` 的使用位置：

> 量词

```js
const str = '-3.1415'
const reg = /^(\+|-)?\d+(\.\d+)?$/ // 表示 0 次或 1 次
const reg = /^[+-]?\d+(\.\d+)?$/
```

> 匹配不捕获

`(?:)` 问号放在分组前面，并且后面紧跟着冒号

```js
const str = '-.31415'
const reg = /^(?:\+|-)?\d+(?:\.(\d+))?$/
```

> 非贪婪性

将问号放在量词后面：`+?`, `*?`, `{}?`, `(+?)`, `(*?)`, `({}?)`

```js
const str = '123456789'
const reg = /\d+?/g
```

> 预查

本身不占宽度，肯定的结果。

特点：
1. 不消耗字符
2. 修饰所在位置的前后
3. 检测任意元字符，任意位数

</details>

## 量词

* `*` 0 次或多次
* `+` 1 次或多次
* `{1,3}` 数量词
* `?` 可选择 
* `|` 交替

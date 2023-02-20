# regexprefer

regexprefer is a memo for helping you find the best regex for a string.

[EN](./README.md) | [CN](./README_CN.md)

## Anchors

* `^` Start of string or line, or in `[]` means not a character
* `$` End of string or line
* `b` Word Boundary
* `B` Non Word Boundary

## Modifiers

* `i` Ignore Case
* `m` Multiline
* `g` Global

## Character Classes

* `[abc]` Character Set
* `[^abc]` Negated Character Set 
* `[a-z]` Range
* `.` Dot 
* `\w` Word
* `\W` Non Word
* `\d` Digit
* `\D` Non Digit
* `\s` Whitespace
* `\S` Non Whitespace

## Groups & References

* `()` Group
* `\1` Reference
* `(?:)` Non Capturing Group

## Quantifiers And Alternation

* `*` Asterisk
* `+` Plus
* `{1,3}` Quantifier
* `?` Optional
* `|` Alternation

## Lookarounds

> `(?=)` Positive Lookahead


```js
const str = '1st 2nd 3rd'
const reg = /\d(?=nd)/g // 2
```

> `(?=)` Positive Lookahead

```js
const str = '1st 2nd 3rd'
const reg = /\d(?!nd)/g // 1 3 
```

> `(?=)` Positive Lookahead

```js
const str = '#1 $5 %8'
const reg = /(?<=%)\d/g // 8 
```

> `(?=)` Positive Lookahead

```js
const str = '#1 $5 %8'
const reg = /(?<!%)\d/g // 1 5 
```

## `?` Summary 

`?` Where to use:

**Classifier**

```js
const str = '-3.1415'
const reg = /^(\+|-)?\d+(\.\d+)?$/ // Indicates 0 or 1 times 
const reg = /^[+-]?\d+(\.\d+)?$/
```

**Matching does not capture**

`(?:)` Non Capturing Group

```js
const str = '-3.1415'
const reg = /^(?:\+|-)?\d+(?:\.(\d+))?$/
```
**Non Greediness**

Put the question mark after the quantifier： `*?` `+?` `{1,3}?`

```js
const str = '12345'
const reg = /\d+?/g
```
**Lookbehind**

It does not occupy the width, and it is a positive result.

characteristic:
1. No character consumption
2. The front and back of the decoration position
3. Detect any metacharacter and any digit

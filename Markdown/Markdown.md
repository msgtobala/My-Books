# Mastering Markdown

##### Paragraphs and Text Decoration

*** Note: Markdown needs a full line break to start a new line

*Italics*

```markdown
Markdown is *cool* or Markdown is _cool_
```

**Bold**

```markdown
Markdown is so **cool** or Markdown is __cool__
```

~~Strike through~~

```markdown
Markdown is so ~~Hard~~
```



##### Headings

# h1

```markdown
This is # h1
```

# h2

```markdown
This is ## h2
```

### h3

```markdown
This is ### h3
```

#### h4

```markdown
This is #### h4
```

###### h5

```markdown
This is ##### h5
```

###### h6

```markdown
This is ###### h6
```



##### Links

<https://github.com/msgtobala/My-Books>

```markdown
<https://github.com/msgtobala/My-Books>
```

[React JS](https://reactjs.org/)

```markdown
[React JS](https://reactjs.org/)
```

[React JS](https://reactjs.org/ "React juide")

```markdown
[React JS](https://reactjs.org/ "React Guide")
```

[React][1]

[1]: https://reactjs.org/	"React Guide"

```markdown
[React][1]
[1]: https://reactjs.org/ "React Guide"
```



##### Images

!['View'](http://unsplash.it/200/200 "This is Tooltip")

```markdown
![Tree](http://unsplash.it/200/200 'This is Tooltip')
```



![Cute Pic][pic]

[Pic]: http://unsplash.it/200/200	"This is Tooltip"

```markdown
![Pic][pic]

[pic]: http://unsplash.it/200/200 "This is a Tooltip"
```

[![](http://unsplash.it/100/100 'Click Me')](http://unsplash.it/500/500)

```markdown
[![](http://unsplash.it/200/200 'Click Me')](http://unsplash.it/500/500)
```

<img src='http://unsplash.it/100/100' alt='Test Image' width='200' height='200'/>

```markdown
<img src='http://unsplash.it/100/100' alt='Test Image' width='200' height='200'/>
```



##### Lists

###### Unordered Lists

* A

* B

* C

  ```markdown
  * A or + A
  * B or + B
  * C or + C
  ```

###### Ordered Lists

1. A
2. B
3. C

``` Mar
1. A
1. B
1. C
```

###### Nested Lists

1. A
   * a
   * b
     + b1
     + b2
       + b21
       + b22

```markdown
1. A
	* a
	* b
		+ b1
		+ b2
			* b21
			* b22
```

###### Texts inside Lists

1. A

   This is inline

```markdown
1. A
   This is inline
```



##### Line Breaks

Markdown is cool. <br/>This is really cool

```markdown
Markdown is cool. <br /> This is really cool
```



###### Horizontal rules

Something

-----

```markdown
Something
----

or 
Something
====
```

##### BlockQuote

> This is Sample Block quote

 ```markdown
> This is Sample Block quote
 ```

> **Block**

```markdown
> **Block**
```

&mdash;

```markdown
&mdash;
```

##### Code blocks

Here is my code

```javascript
var a = 10;
console.log(a);
```

```markdown
​```js
  var a = 10;
  console.log(a);
​```
```



``` var a = 10; ```

```markdown
​``` var a = 10; ```
```

` var a = 10 `

```markdown
` var a = 10; `
```

```diff
- var a = 1;
+ var a = 10;
```

```markdown
​```diff
- var a = 1;
+ var a = 10;
​```
```

##### Tables

| S.No | Name   | Age  |
| ---- | :----- | ---- |
| 1    | Balaji | 21   |

```markdown
| S.No | Name | Age |
|:-----|-----:|:---:|
|1|balaji|21|
```

##### Github Treats

* [x] HTML
* [ ]  CSS
* [x]  JS

```markdown
* [ ] HTML
* [ ] CSS
* [ ] JS
```


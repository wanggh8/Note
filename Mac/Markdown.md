---
title: Markdown 语法
categories: Mac
description: Markdown 语法
cover: /images/MacOS.jpg
---


*   This is the first list item.
*   Here's the second list item.

    > A blockquote would look great below the second list item.

*   And here's the third list item.

---

1.  Open the file.
2.  Find the following code block on line 21:
        
        <html>
          <head>
            <title>Test</title>
          </head>

1. Update the title to match the name of your website.


---
1.  Open the file containing the Linux mascot.
2.  Marvel at its beauty.
    ![Tux, the Linux mascot](https://miro.medium.com/v2/resize:fit:1024/1*ABo4dTsrgA7UboVI7c6yIA.jpeg)
    

<img src="https://miro.medium.com/v2/resize:fit:1024/1*ABo4dTsrgA7UboVI7c6yIA.jpeg" width="50%" height="50%" alt="imagename">


<div align="center">    
<img src="https://miro.medium.com/v2/resize:fit:1024/1*ABo4dTsrgA7UboVI7c6yIA.jpeg" width="200px"
alt="imagename">
</div>

![Tux, the Linux mascot-w200](https://miro.medium.com/v2/resize:fit:1024/1*ABo4dTsrgA7UboVI7c6yIA.jpeg)

1. Close the file.

---
1. First item
2. Second item
3. Third item
    - Indented item
    - Indented item
4. Fourth item

---
This **word** is bold. This <em>word</em> is italic.

---
This is a regular paragraph.

<table>
    <tr>
        <td>Foo</td>
    </tr>
</table>

This is another regular paragraph.

---
这是一个链接 [Markdown语法](https://markdown.com.cn)。
这是一个链接 [Markdown语法](https://markdown.com.cn "最好的markdown教程")。

<https://markdown.com.cn>
<fake@example.com>


I love supporting the **[EFF](https://eff.org)**.
This is the *[Markdown Guide](https://www.markdownguide.org)*.
See the section on [`code`](#code).



---

[1]: https://en.wikipedia.org/wiki/Hobbit#Lifestyle

<!--尽量使用%20代替空格。-->
[link](https://www.example.com/my%20great%20page)

---
At the command prompt, type `nano`.
``Use `code` in your Markdown file.``

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

---
目录1
===============	
Heading level 2
---------------	


---

> #### The quarterly results look great!
>
> - Revenue was off the chart.
> - Profits were higher than ever.
>
>  *Everything* is going according to **plan**.
> 

---

> Dorothy followed her through many of the beautiful rooms in her castle.
>
>> The Witch bade her clean the pots and kettles and sweep the floor and keep the fire fed with wood.

---

Italicized text is the *cat's meow*.
Italicized text is the _cat's meow_.
A*cat*meow	
This text is ***really important***.

---
First line with the HTML tag after.<br>
And the next line.

---

| Syntax      | Description |
| ----------- | ----------- |
| Header      | Title       |
| Paragraph   | Text        |


<!--您可以使用表格的HTML字符代码（&#124;）在表中显示竖线（|）字符。
-->
| Syntax      | Description | Test Text     |
| :---        |    :----:   |          ---: |
| Header      | Title       | Here's this   |
| Paragraph   | Te&#124;xt        | And more      |

---

[Heading IDs](www.baidu.com)	

---
~~世界是平坦的~~ 我们现在知道世界是圆的。

---
- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

---

http://www.example.com
`http://www.example.com`

---

[页面内跳转](#目录1)


<details>
  <summary>点击时的区域标题</summary>

    echo "hello shell"
    echo "hello python"

</details>



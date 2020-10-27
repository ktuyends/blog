---
title: "Test markdown in Blog"
slug: test-markdown-in-blog
date: 2018-05-12

coverImage: /images/life-simple.jpg
coverSize: full
coverMeta: out

Categories:
- Test
Tags:
- Test
showTags: false

gallery:
- /images/gallery1.jpg /images/gallery1.jpg
- /images/gallery2.jpg /images/gallery2.jpg
- /images/gallery3.jpg /images/gallery3.jpg
- /images/gallery4.jpg
- /images/gallery5.jpg
- /images/gallery6.jpg

thumbnailImagePosition: "left"
thumbnailImage: /post/04-test-markdown/markdown.png
clearReading: true	
comments: true
description: "Test"
summary: >
  <p style = "font-family:Roboto; font-weight: 400">Trong này hông có gì đâu, trong này mình chỉ test xem markdown hoạt động tốt hông thôi.</p>
---

Demo markdown in blog
<!--more-->

# Heading 1

## Heading 2

### Heading 3

#### Heading 4

---

## Chèn mục lục

Ta dùng `toc` thay thế cho dấu 3 chấm bên trong: `<!-- ... -->`.

## Mục lục tự tạo

- [Paragraph](#paragraph)
- [Unordered List](#unordered-list-ul)

---
## Paragraph

Paragraph là một đoạn text, [Tesk link](/), **in đậm**, *in nghiêng*, <u>gạch dưới</u>, ~~gạch ngang~~, `hightlight`.

---
## List type

###### Ordered List (ol)

1. List Item 1
2. List Item 2
3. List Item 3

###### Unordered List (ul)

- List Item 1
- List Item 2
- List Item 3

###### Dạng mới
- [ ] Example 1
- [ ] Example 2

---
## Table

|  Header 1  | Header 2   | Header 3   |
|:----------:|------------|------------|
| Division 1 | Division 2 | Division 3 |
| Division 1 | Division 2 | Division 3 |
| Division 1 | Division 2 | Division 3 |
| Division 1 | Division 2 | Division 3 |

---
## Sup, Sub,....
Superscript là chỉ số trên: <sup>superscript</sup>, subscript là chỉ số dưới: <sub>subscript</sub>, acronym là từ viết tắt của một cụm từ dựa trên các chữ cái đầu và được phát âm theo từng chữ cái: <acronym title="National Basketball Association">NBA</acronym>, abbr là chữ viết tắt của một từ, cụm từ và được phát âm như một từ mới: <abbr title="Avenue">AVE</abbr>

---
## Hightlight code

##### Hightlight dạng 1

```python
def test():
if a = b:
```

##### Hightlight dạng 2

`Hight light 1 dòng`

##### Hightlight dạng 3

{{< codeblock lang="python" >}}
# Code here
{{< /codeblock >}}

##### Hightlight dạng 4: Nhiều ngôn ngữ

{{< tabbed-codeblock >}}
<!-- tab R -->
# Code here
<!-- endtab -->
<!-- tab Python -->
# Code here
<!-- endtab -->
<!-- tab SQl -->
Select
Fromt
Where
<!-- endtab -->
{{< /tabbed-codeblock >}}

---
## Mathjax

When $a \ne 0$, there are two solutions to $ax^2 + bx + c = 0$ and they are

$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}$$

---
## Quote

> Quote dạng 1

{{< blockquote "Name" "Source" >}}
Quote dạng 2
{{< /blockquote >}}   

## Pullquote 

Donec non tempus arcu.
Phasellus adipiscing, mauris nec mollis egestas, ipsum nunc auctor velit, et rhoncus lorem ipsum at ante. Duis vel mauris nulla. Maecenas mattis interdum ante, quis sagittis.
{{< pullquote left >}}
Here is a pullquote left. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
{{< /pullquote >}}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas tempus molestie arcu, et
fringilla mauris placerat ac. Nullam luctus bibendum risus. Ut cursus sed ipsum feugiat egestas. Suspendisse elementum, velit eu consequat consequat, augue lorem dapibus libero, eget pulvinar dolor est sit amet nulla. Suspendisse a porta tortor, et posuere mi. Pellentesque ultricies, mi quis volutpat malesuada, erat felis vulputate nisl, ac congue ante tortor ut ante. Proin aliquam sem vel mauris tincidunt, elementum ullamcorper nisl pretium, ultrices cursus justo. Mauris porttitor commodo eros, ac ornare orci interdum in. Cras fermentum cursus leo sed mattis. In dignissim lorem sem, sit amet elementum mauris venenatis ac.
{{< pullquote right >}}
Here is a pullquote right. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
{{< /pullquote >}}
Donec non tempus arcu. Phasellus adipiscing, mauris nec mollis egestas, ipsum nunc auctor velit, et rhoncus lorem ipsum at ante. Duis vel mauris nulla.
Maecenas mattis interdum ante, quis sagittis nibh cursus et. Nulla facilisi. Morbi convallis gravida tortor, ut fermentum enim gravida et. Nunc vel dictum nisl, non ultrices libero.
Proin vestibulum felis eget orci consectetur lobortis. Vestibulum augue nulla, iaculis vitae augue vehicula,
dignissim ultrices libero. Sed imperdiet urna et quam ultrices tincidunt nec ac magna. Etiam vel pharetra elit.

---
## Alert

{{< alert info >}}
Ví dụ 1.
{{< /alert >}}

{{< alert success >}}
Ví dụ 2.
{{< /alert >}}

{{< alert warning >}}
Ví dụ 3.
{{< /alert >}}

{{< alert danger >}}
Ví dụ 4.
{{< /alert >}}

## Hightlight text

* <p>{{< hl-text red >}}highlight red{{< /hl-text >}}</p> 
* **color**: *red, green, blue, purple, orange, yellow, cyan, primary, succes, warning, danger*

---
## Chèn 1 ảnh
<p align="center"><img src="/images/gallery1.jpg" alt="some_text" width="width" height="height"></p>

## Chèn nhiều ảnh

```
{\{< image classes="clear right/left fancybox nocaption fig-nn" src="" title="">}}
# Bỏ dấu \ ở giữa {\{
```
## Chèn video

{{< youtube h5aKoIffRDI>}}

---
### Gallery


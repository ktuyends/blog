---
title: "Chuyển mã Unicode trong R"
slug: string-escape-unicode
date: 2020-08-23
categories:
- Tutorial
tags:
- Tutorial
showTags: false
thumbnailImagePosition: "left"
thumbnailImage: /post/03-tutorial/img/cover/encoding.jpg
clearReading: true
metaAlignment: center	
comments: true
description: "Tutorials"
summary: >
  Với những người lập trình R trên môi trường Windows, một trong những nhược điểm thường gặp là lỗi hiển thị Tiếng Việt. Có hai cách để giải quyết vấn đề này...
---

Với những người lập trình R trên môi trường Windows, một trong những nhược điểm thường gặp là lỗi hiển thị Tiếng Việt. Có hai cách để giải quyết vấn đề này. Một là các bạn chuyển qua môi trường Linux. Cách thứ hai là chuyển đổi mã Unicode sang dạng Escape. Ngoài ra còn cách nào khác nữa không, tạm thời tôi chưa tìm hiểu được. Nếu bạn biết, hãy chia sẻ với tôi nha.

Vì tạm thời, tôi vẫn phải sử dụng môi trường Windows, nên tôi sử dụng cách thứ 2 để xử lý khi gặp lỗi này. Cách đơn giản nhất để chuyển đổi các ký tự Unicode sang dạng Escape là tạo một file dạng `.html`. Với file này, các bạn có thể sử dụng kể cả khi không có kết nối Internet.

Đây là nội dung của file `html`. Tôi đặt tên file này là `escape-unicode.html`:

```
<!DOCTYPE html>
<html>

<head>
    <title>Convert to escape string</title>
    <meta charset="utf-8" />
</head>
<style>
    .panel {
        display: block;
        width: 50%;
    }
    
    textarea {
        height: 150px;
        width: 100%;
    }
    
    .align_right {
        text-align: right;
    }
</style>
```

```
<script>
    /* ASCII code: http://ascii-table.com/codepage.php?1252 */
    /* escape: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/escape */
    /* encodeURI: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURI */
    /* encodeURIComponent: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent */

    function toEscape() {

        var sourceString = document.getElementById("inputString").value;
        var escapeString = "";
        document.getElementById("outputOriginalString").value = escape(sourceString);

        for (var i = 0; i < sourceString.length; i++) {
            var code = sourceString.charCodeAt(i);
            if (code >= 0xFF) {
                escapeString += escape(sourceString.charAt(i)).replace("%u", "\\u");
            } else {
                escapeString += sourceString.charAt(i);
            }
        }
        document.getElementById("outputConvertedString").value = escapeString;
    }
</script>

<body>
    <div class="panel">
        <div>Nhập chuỗi Unicode</div> <textarea id="inputString"></textarea><br />
        <div class="align_right"> <button type="button" id="escapeButton" title="Escape" onclick="toEscape();">Chuyển mã</button> </div>
        <div>Xuất chuỗi Escape</div> <textarea id="outputOriginalString"></textarea></br>
        </br>
        <div>Xuất chuỗi Escape (không chuyển ASCII code)</div> <textarea id="outputConvertedString"></textarea> </div>
</body>

</html>
```

Và đây, là kết quả khi bạn mở file `escape-unicode.html`:

<script>
    /* ASCII code: http://ascii-table.com/codepage.php?1252 */
    /* escape: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/escape */
    /* encodeURI: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURI */
    /* encodeURIComponent: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent */

    function toEscape() {

        var sourceString = document.getElementById("inputString").value;
        var escapeString = "";
        document.getElementById("outputOriginalString").value = escape(sourceString);

        for (var i = 0; i < sourceString.length; i++) {
            var code = sourceString.charCodeAt(i);
            if (code >= 0xFF) {
                escapeString += escape(sourceString.charAt(i)).replace("%u", "\\u");
            } else {
                escapeString += sourceString.charAt(i);
            }
        }
        document.getElementById("outputConvertedString").value = escapeString;
    }
</script>

<body>
    <div class="panel">
        <div>Nhập chuỗi Unicode</div> <textarea id="inputString"></textarea><br />
        <div class="align_right"> <button type="button" id="escapeButton" title="Escape" onclick="toEscape();">Chuyển mã</button> </div>
        </br>
        <div>Xuất chuỗi Escape</div> <textarea id="outputOriginalString"></textarea></br>
        </br>
        <div>Xuất chuỗi Escape (không chuyển ASCII code)</div> <textarea id="outputConvertedString"></textarea> </div>
</body>

---

P/s: Ôi cái kết quả hiển thị trên Blog của tôi nó hơi xấu so với dự định. Khi các bạn mở trực tiếp file nhìn nó sẽ đẹp hơn thế này. Bài viết này đến đây là kết thúc. Nội dung trong file trên mình lấy từ bài viết của anh [Trát Quang Thụy](https://rpubs.com/BabyMouse/escapeString). 

---
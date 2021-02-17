---
title: "Introduction to Git"
slug: intro-to-git
date: 2016-04-05
categories:
- Blog
tags:
- Blog
showTags: false
thumbnailImagePosition: "left"
thumbnailImage: /post/03-tutorial/img/cover/git.png
clearReading: true
metaAlignment: center
comments: true
description: "Blog"
summary: >
  Version control là một công cụ mạnh mẽ giúp chúng ta theo dõi, quản lý các phiên bản của code, phục hồi khi code bị lỗi,...Trong bài này, tôi viết về Git, một công cụ version control phổ biến nhất. 
---

Version control là một công cụ mạnh mẽ giúp chúng ta theo dõi, quản lý các phiên bản của code, phục hồi khi code bị lỗi,...Trong bài này, tôi viết về Git, một công cụ version control phổ biến nhất. 

## 1. Giới thiệu

Git là một hệ thống quản lý phiên bản, được sử dụng để quản lý source code. Trên Git, các phiên bản – trạng thái được lưu lại và ta có thể đưa source code về trạng thái – phiên bản cũ khi cần thiết.

Chuỗi bài viết này tôi không đi trình bày chi tiết về Git, tôi chỉ ghi lại một số câu lệnh hay dùng, vì cũng không biết khi nào tôi mới dùng đến nó. Các vấn đề như cài đặt Git, đăng ký tài khoản Github như thế nào có thể dễ dàng tìm kiếm trên Google và Youtube với đầy đủ các hướng dẫn chi tiết.

## 2. Cài đặt Git

Để cài đặt Git các bạn vào trang sau và download phiên bản phù hợp với hệ điều hành của mình về rồi sau đó tiến hành cài đặt: [Git SCM](https://git-scm.com/download/win)

<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git1.bmp" style="width: 513px;"></p>

**Cài đặt:**

<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git2.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git3.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git4.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git5.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git6.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git7.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git8.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git9.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git10.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git11.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git12.bmp"></p>

P/s: Các hình ảnh trong note này tôi lấy trên trang: https://o7planning.org 

## 3. Command line cơ bản

Khi làm việc với Git, ta thường thực hiện các thao tác sử dụng câu lệnh trên Git bash (window) hoặc terminal (linux). Mặc dù cũng có các GUI hỗ trợ việc thực hiện Git nhưng tài liệu này không đi về việc sử dụng GUI. Để làm việc với Git bash, terminal ta cần biết một số câu lệnh thao tác với folders và files trên máy tính.

*Di chuyển đến các thư mục ta sử dụng lệnh `cd`:*

```shell
$ cd
$ cd path
$ cd folder_name
```

Trong trường hợp tên thư mục có dấu cách, ta đặt `path` và `folder_name` trong dấu ngoặc kép: `"path"`, `"folder_name"`. 

*Để di chuyển trở lại vị trí cũ ta sử dụng:*

```shell
$ cd -
```

*Để di chuyển lên thư mục chứa thư mục hiện tại ta sử dụng:*

```shell
$ cd ..
```

*Show các file and folders ở thư mục hiện hành với `ls`:*

```shell
$ ls
$ ls -1
```

*Tạo một folders mới với `mkdir`:*

```shell
$ mkdir folder_name
```

*Tạo một file với `touch` and `echo`:*

```shell
$ touch NewFile_1.txt NewFile_2.txt ...NewFile_n.txt
$ echo "Text add to file" >> NewFile_1.txt
```

Câu lệnh trên tạo ra các file và ghi nội dung vào các file đó, chúng ta có thể sử dụng `path/file_name.txt` thay vì `file_name.txt`. Lệnh `echo` sẽ tạo ra file mới và ghi nội dụng vào file mới nếu file đó chưa tồn tại.

*Xóa files:*

```shell
$ rm -i "file_name"
```

*Xóa các thư mục rỗng:*

```shell
$ rmdir "folder_name"
```

*Xóa các thư mục không rỗng:*

```shell
$ rm -rf "folder_name"
```

## 4. Git Configure

Sau khi cài đặt Git, bước đầu tiên chúng ta cần làm là cài đặt Git config. Sử dụng Git-bash hoặc terminal với các lệnh sau để cài đặt Git config. Git config chính là thông tin khi chúng ta push source code lên trên remote. Còn push là gì, remote là gì tôi sẽ giải thích sau.

```shell
$ git config --global user.name <”User Name”> 
$ git config --global user.email <UserEmailAddress>
$ git config --list
```

## 5. Đăng ký tài khoản Github

Đầu tiên các bạn vào trang web của [Github](https://github.com/) sau đó đăng ký cho tôi một tài khoản. Cách đăng ký thì như các trang khác thôi, không có vấn đề gì khó khăn cả.

## 6. Cài đặt Github Desktop

Đầu tiên, các bạn cần download [Github Desktop](https://desktop.github.com/).

Sau khi download xong các bạn cài đặt như phần mềm bình thường thôi. Hình như Github desktop yêu cầu hệ điều hành 64 bit thì phải. Máy tôi cùi quá không cài đặt được Github desktop nên tôi chủ yếu xài command lines. 

Để bắt đầu với Github desktop các bạn khởi động chương trình và chọn Sign to Github.com

<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git13.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git14.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git15.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-02-gioi-thieu-git-va-github/git16.bmp"></p>

OK. Vậy là bạn đã cài đặt và đăng nhập xong vào Github desktop rồi đó.

## 7. Giới thiệu Gitflow

Trước khi nói về quy trình làm việc, tôi muốn các bạn hiểu sơ sơ một số khái niệm cơ bản gồm Remote, local, branch, branch master. Còn về chi tiết, tôi sẽ giải thích ở các bài sau. 

Tôi gọi local là nơi lưu trữ các phiên bản của code trên máy tính của tôi. Remote là một nơi để để lưu trữ code của tất cả mọi người trong một team với nhau. Ví dụ mỗi người trong team lập trình một chức năng nào đó. Sau đó gửi code lên remote để hợp nhất các chức năng của tất cả mọi người lại với nhau.  Nếu bạn vẫn thấy khó hiểu thì cứ tạm hiểu nó giống như google drive ý, là nơi tôi up tài liệu, up code lên.

Khái niệm tiếp theo là branch master. Master ta hiểu đơn giản là một nhánh – branch lưu trữ code hay còn gọi là nhánh chính. Khi chúng ta muốn tạo ra các tính năng mới, ta làm việc ở một branch khác. Sau khi check, test ổn định rồi ta đem gộp vào nhánh chính. 

Nếu các bạn thấy khó hiểu về nhánh - branch, các bạn cứ tưởng tượng giả sử ta cần làm một cái bàn. Ta gọi branch master là nơi ta lắp ráp cái bàn. Còn branch là nơi ta làm các bộ phận của cái bàn như mặt bàn, chân bàn,…Sau khi làm xong ta đem về branch master để lắp ráp lại.

Trước khi đi vào giải thích chi tiết về các câu lệnh Git, tôi muốn trình bày một quy trình làm việc với Git trước. Dĩ nhiên là mỗi công ty có thể sẽ có một quy trình làm việc riêng. Và đây cũng chỉ là một quy trình trong số rất nhiều quy trình mà thôi. 

<p align="center"><img src="/post/03-tutorial/03-git/bai-03-gioi-thieu-gitflow/git17.bmp"></p>

Quay lại với quy trình làm việc với Git. Về cơ bản sẽ gồm một số bước như sau:

*	Bước 1: Tạo một remote repository của project trên Github của project. Ta gọi remote repository này là upstream remote.
*	Bước 2: Fork upstream remote về Github cá nhân. Ta gọi remote repository này là origin remote.
*	Bước 3: Clone origin remote về local để làm việc. Ta gọi đây là local repository.
*	Bước 4: Tạo branch ở local repository để phát triển các chức năng. Sau khi hoàn thành các tính năng ta tiến hành các bước tiếp theo.
*	Bước 5: Pull code từ upstream remote về branch master ở local repository để cập nhật các thay đổi từ upstream.
*	Bước 6: Merge code của branch master vào nhánh của các chức năng.
*	Bước 7: Xử lý conflict – xung đột code nếu có.
*	Bước 8: Push nhánh sau khi đã giải quyết conflict lên origin remote.
*	Bước 9: Gửi Pull request đến upstream remote để merge code vào dự án.
*	Bước 10: Sau khi check và test code ok. Tiến hành gán tag và release. 

Các bước này tạm thời các bạn có thể chưa hiểu, nhưng các bạn có thể đọc lại sau khi đã đọc các bài sau.

## 8. Summary

Tổng hợp lại, trong bài này tôi đã giới thiệu cơ bản về Git gồm:

- Cài đặt Git và Github.
- Một số command line như `cd`, `mkdir`, `echo`,...
- Gitflow và một số khái niệm như remote, branch,...

---


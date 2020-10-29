---
title: "Git: Working with Remotes"
slug: working-with-git-remotes
date: 2016-04-19
categories:
- Tutorial
tags:
- Tutorial
showTags: false
thumbnailImagePosition: "left"
thumbnailImage: /post/03-tutorial/img/cover/github.png
clearReading: true
metaAlignment: center	
comments: true
description: "Tutorial"
summary: >
  Git remote thường được sử dụng để chia sẻ source code giữa các thành viên trong cùng một dự án, về cơ bản quy trình làm việc với remote sẽ như sau...
---

## 1. Làm việc với Remote

Git remote thường được sử dụng để chia sẻ source code giữa các thành viên trong cùng một dự án, về cơ bản quy trình làm việc với remote sẽ như sau:

*	Git fetch: Lấy code từ trên server về, để vào một branch có dạng remote/branch.
*	Git merge: Gộp code từ remote/branch vào master branch.
*	Git add and git commit nếu xảy ra conflict.
*	Git push <remote_name> <branch_name>: Đẩy code lên server.

**Thêm/Xóa một remote:**


```shell
$ # Liệt kê danh sách remote
$ git remote
$ git remote -v
```

```shell
$ # Thêm một remote
$ git remote add <remote_name> <url>
```

```shell
$ # Xem thông tin remote
$ git remote show <remote_name>
```

```shell
$ # Đổi tên remote
$ git remote rename <old_name> <new_name>
```

```shell
$ # Xóa một remote
$ git remote rm <remote_name>
```

**Làm việc với remote:**

```shell
$ # Push
$ git push origin master

$ # Fulll push
$ git push origin local_branch:remote_branch

$ # download source code từ remote
$ # Git fetch sẽ lấy tất cả các branch trên remote về local 
$ git fetch remote_name

$ # Đồng bộ local và remote
$ git checkout master
$ git merge origin/master
```

**Làm việc với Remote Branch:**

Remote branch là các tham chiếu đến trạng thái của các branch tại remote repo. Chúng là các nhánh nội bộ mà chúng ta không thể thực hiện di chuyển chúng.

Remote branch có dạng:  `(remote)/(branch)`.

Để dễ hình dung, ta xem xét ví dụ dưới đây:

<p align="center"><img src="/post/03-tutorial/03-git/bai-07-lam-viec-voi-remote/git50.bmp"></p>

Khi chúng ta thực hiện clone từ server về local, Git sẽ đặt một con trỏ, trỏ tới nhánh master của origin và đặt tên là `origin/master`. Chúng ta không thể di chuyển nhánh này. Đồng thời Git cũng tạo riêng cho chúng ta một nhánh master – local branch để chúng ta làm việc.

<p align="center"><img src="/post/03-tutorial/03-git/bai-07-lam-viec-voi-remote/git51.bmp"></p>

Bây giờ, giả sử trên server một vài người đã đẩy các commit mới lên, nó sẽ trông như hình trên.

Đồng thời ở dưới local, chúng ta cũng thực hiện một số commit mới trên nhánh master. Tuy nhiên nhánh `origin/master` thì không di chuyển cho đến khi ta cập nhật từ server về:

<p align="center"><img src="/post/03-tutorial/03-git/bai-07-lam-viec-voi-remote/git52.bmp"></p>

Tiếp theo chúng ta kéo những thay đổi trên server về, kết quả sẽ như sau:

<p align="center"><img src="/post/03-tutorial/03-git/bai-07-lam-viec-voi-remote/git53.bmp"></p>

**Push các nhánh lên remote:**

```shell
$ # Ví dụ:
$ # Hãy sử dụng nhánh local serverfix của tôi và đẩy nó lên để cập nhật nhánh 
$ # remote serverfix 
$ git push origin serverfix

$ # Đẩy nhánh local serverfix vào nhánh remote awesomebranch
$ git push origin serverfix:awesomebranch
```

**Cập nhật nội dung từ nhánh remote:**

```shell
$ # Giả sử ta fetch từ remote về
$ git fetch origin
remote: Counting objects: 20, done.
remote: Compressing objects: 100% (14/14), done.
remote: Total 15 (delta 5), reused 0 (delta 0)
Unpacking objects: 100% (15/15), done.
From git@github.com:schacon/simplegit
 * [new branch]      serverfix    -> origin/serverfix
```

Khi ta thực hiện fetch từ remote về, Git không tạo ra nhánh local serverfix mới mà chỉ tạo ra một nhánh tham chiếu đến nhánh serverfix trên remote. Chúng ta không thể chỉnh sửa nhánh `origin/serverfix` này.

Để tích hợp nhánh remote vào nhánh hiện tại:

```shell
$ git merger origin/serverfix
```

Nếu chúng ta muốn có một nhánh serverfix riêng để có thể làm việc với nó, ta có thể tách serverfix ra khỏi nhánh remote bằng cách:

```shell
$ git checkout -b serverfix origin/serverfix 
```

Cách này sẽ tạo ra nhánh local serverfix cùng vị trí với nhánh origin/serverfix.

**Xóa nhánh trên remote:**

```shell
$ # Xóa nhánh serverfix trên remote
$ git push origin :serverfix
```

## 2. Làm việc với Tag

```shell
$ # Tạo tag với commit hiện tại
$ git tag -a V1.1 -m "message tag"

$ # Tạo tag với một commit cụ thể
$ git tag -a V1.1 <hash commit> -m "message tag"
```

```shell
$ # Xem thông tin tag
$ git tag
$ git show V1.1
```

```shell
$ # Push tag
$ git push origin V1.1

$ # Day tat ca cac tag
$ git push origin --tags
```

```shell
$ # Create branch from a tag
$ git checkout -b <branch_name> <tag> 
```

```shell
$ # Fetch tag
$ git fetch
$ git fetch --tags origin
```

```shell
$ # Delete a local tag
$ git tag -d <tag_name>

$ # Delete all local tags.
$ git tag -d $(git tag -l)
```

```shell
$ # Delete all remote tags.
$ git push origin --delete $(git tag -l) 
```

## 3. Summary

{{< youtube 7lcUQLQEHKA>}}

---
---
title: "Basic Git"
slug: basic-git
date: 2016-04-13
categories:
- Blog
tags:
- Blog
showTags: false
thumbnailImagePosition: "left"
thumbnailImage: /post/03-tutorial/img/cover/git-basic.png
clearReading: true
metaAlignment: center
comments: true
description: "Blog"
summary: >
  Với quy trình Gitflow đã trình bày trong bài trước, về cơ bản tôi sẽ chia quá trình học Git làm hai phần. Phần một, cách sử dụng Git để quản lý code ở Local. Phần hai...
---

Với quy trình Gitflow đã trình bày trong bài trước, về cơ bản tôi sẽ chia quá trình học Git làm hai phần:

- Phần 1: Làm việc ở local.
- Phần 2: Làm việc với remote.

Trong bài này, chúng ta sẽ đi tìm hiểu về cách sử dụng Git để quản lý code ở local. Còn về làm việc với remote, tôi sẽ trình bày nốt trong bài tiếp theo. Tuy nhiên, trước khi đi vào từng nội dung cụ thể, ta làm một số thao tác chuẩn bị cơ bản đã. Bắt đầu nào!

## 1. Chuẩn bị

**Bước 1: Tạo Remote repository – upstream**

Với bước này, các bạn có thể xem hình minh họa bên dưới:

<p align="center"><img src="/post/03-tutorial/03-git/bai-04-chuan-bi/git18.bmp" style="width: 512px;"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-04-chuan-bi/git19.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-04-chuan-bi/git20.bmp"></p>

**Bước 2: Fork upstream repository về trang GitHub cá nhân**

**Bước 3: Clone origin repository về local và kết nối với upstream remote**

Khi clone một repository về, local repository sẽ được liên kết với remote repository mà nó clone về. Sử dụng câu lệnh:

```shell
$ cd <local_repo_folder>
$ git clone <url>
```

Bước tiếp theo trước khi bắt đầu vào các công việc chính, chúng ta cần liên kết local repository với upstream remote để có thể cập nhật các thay đổi trên upstream remote về local.

```shell
$ # Kết nối local repository với remote
$ git remote add <remote_name> <path/my_project.git>

$ # Danh sách các remote repository
$ git remote -v
```

```shell
$ # Add remote upstream
$ git remote add upstream <url>
$ git remote –v
```

## 2. Làm việc với Local

Như vậy, là tôi đã trình bày xong một số bước chuẩn bị cơ bản, luôn luôn phải làm trước bạn bắt đầu một dự án. Và chúng ta chỉ phải làm một lần duy nhất mỗi khi lập một dự án mới. Từ phần này trở đi là các công việc thường xuyên lặp đi lặp lại khi làm việc với source code.

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git21.bmp"></p>

Quy trình làm việc của Git tại local gồm 3 bộ phận:

*	Working Directory: Thư mục chứa các files của project trên máy tính.
*	Stage (Index): Nơi xác nhận các files sẽ được commit tới History (Repository).
*	History (Repository): Nơi lưu trữ các phiên bản (snap shot) được commit đến.

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git22.bmp"></p>

**Thêm các files vào Stage (Index):**

```shell
$ git add file1 file2 ... filen
$ git add somefolder
$ git add . # add tất cả các files
```

Nếu một files đã được thêm vào Stage (Index) sau đó chúng ta lại chỉnh sửa files đó, thì chúng ta phải add lại files đó để thông báo cho Git biết sự thay đổi nếu không Git sẽ lưu trữ phiên bản cũ – chưa thay đổi, thay vì phiên bản mới – vừa thay đổi.

```shell
$ # Examp
$ edit somefile.txt
$ git add somefile.txt
```

**Commit:**

```shell
$ # lưu vào repository kèm theo thông tin ghi chú
$ git commit -m "Initial commit"
```

Trong trường hợp ta đã commit, nhưng muốn thêm một số files vào commit vừa commit hoặc sửa đổi message của commit đó ta sử dụng:

```shell
$ git commit --ammend "Ammend the commit"
```

**Git status:**

```shell
$ git status
```

Git status được sử dụng để xem trạng thái của các files:

*Trạng thái 1: Các files sẵn sàng để commit.*

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git22a.bmp"></p>

*Trạng thái 2: Đã được theo dõi nhưng bị sửa đổi, để thêm các sửa đổi này ta cần add lại.*

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git23.bmp"></p>

*Trạng thái 3: Các files chưa được theo dõi – chưa được add*

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git24.bmp"></p>

**Thực hiện commit bỏ qua bước git add đối với các files bị sửa đổi:**

Trường hợp các files được thêm vào stage (index) hoặc đã commit mà bị sửa đổi, nếu muốn bỏ qua bước `git add` ta có thể sử dụng câu lệnh:

```shell
$ git commit -a -m "commit message"
```

**Lịch sử Commit:**

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git25.bmp"></p>

Mỗi lần chúng ta thực hiện commit, git sẽ tạo ra một commit mới dưới dạng SHA và trỏ về commit trước, commit trước được gọi là parent commit.

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git26.bmp"></p>

Master là nhánh chính, maint là nhánh phụ - được biểu diễn bằng màu cam. Màu xanh là các commit. HEAD là một tham chiếu được sử dụng để xác định nhánh, commit hiện tại mà chúng ta đang ở tại đó. Trong hình trên nhánh hiện tại là nhánh Master, đang trỏ về commit mới nhất ed489, a47c3 là commit đầu tiên trong hình trên.

**Quá trình commit 1:**

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git27.bmp"></p>

Khi chúng ta thực hiện commit, Git tạo một commit mới – f0cec đối với các files từ khu vực Stage (Index) và đặt commit hiện tại làm cha – ed489. Sau đó nhánh hiện tại trỏ đến commit này – HEAD – Master.

**Quá trình commit Ammend:**

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git28.bmp"></p>

**Quan sát commit log:**

```shell
$ # liệt kê danh sách commit
$ git log

$ # liệt kê theo định dạng một dòng đơn giản
$ git log --oneline

$ # liệt kê theo dạng đồ thị
$ git log --oneline --graph --all --decorate

$ # hiển thị nội dung commit
$ git show 8387276
```

**Quan sát sự thay đổi:**

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git29.bmp"></p>

```shell
$ # xem những thay đổi của một file xác định
$ git diff first_file.txt
 
$ # xem những thay đổi của một file xác định tại một thời điểm commit bất kì
$ git diff 9a98bc98 first_file.txt
```

## 3. Reset, checkout and revert

Reset, checkout và revert là 3 khái niệm khá là lằng nhằng và dễ nhầm lẫn trong Git. Ba từ khóa này thường được sử dụng trong việc phục hồi code. Tuy nhiên trước tiên chúng ta phải hiểu được Working Directory, Index (staged) và Repository – Commit – History. Sau đó chúng ta cần hiểu 3 bước liên quan đến các từ khóa này:

*	Bước 1: HEAD có di chuyển hay không.
*	Bước 2: Index (Staged) có thay đổi hay không.
*	Bước 3: Working Directory có thay đổi hay không.

#### 3.1. Tìm hiểu về Checkout

Lệnh `Checkout` có 4 tác dụng:

*	Di chuyển qua lại giữa các Branch.
*	Nhảy HEAD đến một commit nào đó.
*	Sao chép các tệp từ history đến index và working directory.
*	Sao chép các tệp từ index đến working directory.

**Trường hợp 1:** Giả sử các files đã được Git theo dõi, sau đó các files bị sửa đổi, chưa được Git add đến index.

Đối với tình huống này, sau khi sửa đổi chúng ta cảm thấy có vấn đề và muốn hủy bỏ sự thay đổi hay nói cách khác là muốn quay trở lại phiên bản trước khi thay đổi, khi đó chúng ta sử dụng: 

```shell
$ git checkout -- files
```

Câu lệnh trên sẽ sao chép phiên bản trước khi sửa đổi ở index và đè vào working directory:

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git30.bmp"></p>

**Trường hợp 2:** Giả sử các files đã được Git theo dõi, chúng ta thực hiện sửa đổi và đã add nó vô Index.
Đối với tình huống này, nếu chúng ta muốn phục hồi lại phiên bản trước khi sửa đổi ta có thể sử dụng câu lệnh:

```shell
$ git checkout HEAD~n -- files
```

Câu lệnh trên sẽ thực hiện quy trình sau:

*	Bước 1: HEAD không thay đổi.
*	Bước 2: Sao chép các tập tin từ commit trước HEAD n lần tới Index.
*	Bước 3: Sao chép các tập tin từ commit trước HEAD n lần tới working directory. 

Nếu chúng ta muốn sao chép các tập tin tại commit mới nhất đến Index và working directory chúng ta sử dụng:

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git31.bmp"></p>

**Trường hợp 3:** Sao chép các tập tin từ commit cha của commit hiện tại:

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git32.bmp"></p>

**Trường hợp 4:** Chuyển nhánh

Khi thực hiện chuyển nhánh, Git sẽ thay thế các files ở working directory và index trong nhánh cũ (commit cũ) bằng các files trong nhánh chuyển đến (commit chuyển đến). Các files nào không nằm trong cả hai nhánh, Git sẽ bỏ qua. Các files nào nằm trong nhánh cũ (commit cũ) mà không nằm trong nhánh chuyển đến (commit chuyển đến) Git sẽ xóa bỏ. Khi chúng ta chuyển ngược lại về nhánh cũ, thì Git lại thiết lập lại working directory và index sao cho khớp với nhánh cũ.

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git33.bmp"></p>

**Trường hợp 5:** Không chỉ ra tên tệp tin, không checkout đến một nhánh, checkout đến một commit, SHD – id, tag, remote, master~n

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git34.bmp"></p>

Đây là trường hợp HEAD tách rời với nhánh, khi chúng ta chuyển đến một commit, Stage và Working Directory cũng được cập nhật để phù hợp với commit đó. Khi HEAD bị tách rời, nếu chúng ta thực hiện commit ở đây sẽ hơi khác so với quy trình commit phía trên.

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git35.bmp"></p>

Khi thực hiện commit, một nhánh mới vô danh được tạo ra. Một khi chúng ta checkout một cái gì đó khác, commit này không được tham chiếu đến, nó sẽ bị xóa bỏ:

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git36.bmp"></p>

Mặt khác, nếu muốn lưu trữ lại trạng thái commit này, chúng ta tạo ra một nhánh mới có tên cụ thể cho nó:

```shell
$ git checkout -b branch_name
```

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git37.bmp"></p>


**Tóm Tắt:**

Khi thực hiện: `$ git checkout [commit]/[branch]`

*	HEAD dịch chuyển đến vị trí mới.
*	Working directory và Index được cập nhật để phù hợp.
*	Working directory an toàn.

Khi thực hiện: `$ git checkout [Commit] -- files`

*	HEAD không bị chuyển.
*	Các files đã lựa chọn ở trên được phục hồi ở working directory và index.
*	Working directory không an toàn vì HEAD không dịch chuyển.

#### 3.2. Tìm hiểu về Reset

Lệnh reset sẽ dịch chuyển nhánh hiện tại tham chiếu đến một vị trí khác, khác với checkout chỉ di chuyển HEAD thay vì di chuyển tham chiểu của nhánh. Lệnh reset cũng có các option được sử dụng để sao chép các files từ repository – history đến index và working directory.

```shell
$ # Chỉ dịch chuyển commit, index và working directory không đổi
$ git reset --soft HEAD~n

$ # Dịch chuyển commit, cập nhật index, working directory không đổi
$ git reset HEAD~n

$ # Dịch chuyển commit, cập nhật index và working directory
$ git reset --hard HEAD~n
```

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git38.bmp"></p>

Nếu một commit không được chỉ định, thì commit mặc định là commit hiện tại:

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git39.bmp"></p>

**Trường hợp File level:**

```shell
$ # HEAD không dịch chuyển, Index thay đổi, Working directory không đổi
$ git reset -- files
$ git reset HEAD~n --files
```

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git40.bmp"></p>

**Tóm tắt:**

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git41.bmp"></p>

#### 3.3. Tìm hiểu về Revert

Giả sử bạn đã thực hiện các commit và muốn quay trở lại một commit nào đó trong quá khứ, lệnh revert được sử dụng để tạo ra một commit tương đương commit trong quá khứ:

Ví dụ:

```shell
$ git checkout hotfix
$ git revert HEAD~2
```

<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git42.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-05-lam-viec-voi-local/git43.bmp"></p>

## 4. Làm việc với Branch

Nhánh là một khái niệm mới trong Git. Giả sử chúng ta muốn thử nghiệm một tính năng mới, ta tạo một nhánh, chuyển qua nhánh đó làm việc, sau khi cảm thấy an tâm ta chuyển về nhánh chính và gộp các tính năng mới vào nhánh chính. Nhánh chính – mặc định trong Git là nhánh master. Một nhánh luôn chỉ đến một commit nào đó.

**Xem danh sách các nhánh:**

```shell
$ # Hiển thị danh sách nhánh
$ git branch

$ # Hiển thị danh sách nhánh và commit nó chỉ vào
$ git branch -v
```

**Tạo nhánh mới:**

```shell
$ # Nếu không có commit, nhánh mới trỏ đến commit hiện tại
$ git branch branch_name [commit]
```

**Di chuyển giữa các nhánh:**

```shell
$ git checkout branch_name
```

**Gộp nhánh:**

```shell
$ # Gộp nhánh new_branch vào nhánh master
$ git checkout master
$ git merge new_branch
```

Khi thực hiện merge, Git sẽ tạo ra một commit mới, nếu không có conflict, Git sẽ tạo ra một commit mới chứa sự thay đổi ở cả hai nhánh.

**Giải quyết conflict:**

Conflict xảy ra khi ta sửa cùng lúc một file ở 2 nhánh, sau đó gộp chúng lại với nhau. Khi xảy ra conflict ta mở file xảy ra conflict và chỉnh sửa files, giữ lại nội dung chúng ta sẽ lấy:

<p align="center"><img src="/post/03-tutorial/03-git/bai-06-lam-viec-voi-branch/git44.bmp"></p>

Chúng ta phải xóa đi các dòng như `<<<<<< HEAD`, `>>>>>> branch`, và `============`

Sau khi chỉnh sửa xong files bị conflict ta add lại:

```shell
$ git add somefile.txt
$ git commit
```

**Xóa nhánh:**

Sau khi đã làm việc và merge nhánh xong, nếu không cần sử dụng nữa chúng ta nên xóa nhánh đi:

```shell
$ git branch -d branch_name
```

**Các trường hợp đặc biệt đối với merge:**

Trường hợp 1: Các commit gộp vào commit hiện tại là commit tổ tiên của commit hiện tại thì không xảy ra điều gì.

Trường hợp 2: Commit hiện tại là commit tổ tiên của các commit khác, merge đơn giản chỉ là dịch chuyển tham chiếu và commit mới được checkout:

<p align="center"><img src="/post/03-tutorial/03-git/bai-06-lam-viec-voi-branch/git45.bmp"></p>

**Quy trình merge đối với các trường hợp khác:**

<p align="center"><img src="/post/03-tutorial/03-git/bai-06-lam-viec-voi-branch/git46.bmp"></p>

Đầu tiên commit hiện tại – ed489, commit khác – 33104 và commit tổ tiên – b325c được gộp lại theo 3-way merge, Working Directory và Stage (Index) được cập nhật. Nếu không xảy ra conflict thì tạo ra một commit mới, commit này tham chiếu đến hai commit cha – 33104 và ed489.

**Cherry Pick:**

Lệnh cherry-pick sẽ sao chép một commit, tạo một commit mới trên nhánh hiện tại với nội dung giống hệt commit sao chép:

<p align="center"><img src="/post/03-tutorial/03-git/bai-06-lam-viec-voi-branch/git47.bmp"></p>

**Rebasing:**

Lệnh rebase có chức năng giống như lệnh merge tuy nhiên cơ chế hoạt động và các bước thực hiện của nó khác so với merge. Sau này nếu làm việc với nhánh có thể tìm hiểu thêm về rebasing.

<p align="center"><img src="/post/03-tutorial/03-git/bai-06-lam-viec-voi-branch/git48.bmp"></p>
<p align="center"><img src="/post/03-tutorial/03-git/bai-06-lam-viec-voi-branch/git49.bmp"></p>

**Stash:**

Git stash được sử dụng khi muốn lưu lại các thay đổi chưa commit, thường rất hữu dụng khi chúng ta muốn đổi sang một branch khác mà lại đang làm dở ở branch hiện tại.

```shell
$ # Lưu lại toàn bộ nội dung công việc đang làm dở
$ git stash save

$ # Hiển thị danh sách stash đã lưu
$ git stash list
$ git stash list -p
```

```shell
$ # quan sát nội dung của stash cụ thể, index bắt đầu từ 0
$ git stash show stash@{0}
$ git stash show -p stash@{0}
```

```shell
$ # Lấy stash ra và đưa vào working directory
$ git stash apply stash@{0}
```

```shell
$ # Xóa stash
$ git stash drop stash@{0}

$ # Xóa tất cả stash
$ git stash clear

$ # apply + drop stash
$ git stash pop stash@{0}
```

**Quản lý các nhánh:**

```shell
$ # Xem các nhánh
$ git branch 
$ git branch -v
$ git branch --merged
$ git branch --no-merged
```

```shell
$ # Xóa nhánh khi chưa merged
$ git branch -D testing
```

## 5. Summary

Như vậy là, trong post này, tôi đã giới thiệu 3 nội dung chính khi sử dụng Git để quản lý code ở local gồm:

- Câu lệnh cơ bản nhât: `git add`, `git commit`,...
- Phục hồi code với reset, revert và checkout.
- Làm việc với branch trong Git.

---

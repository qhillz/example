# Git 기초

* 분산버전관리시스템(DVCS)

## 로컬 저장소 설정

~~~ bash
$ git init
Initialized empty Git repository in E:/Desktop/정리/.git/

(master) $
~~~

* `.git` 폴더가 생성되고, 여기에 git과 관련된 모든 정보들이 저장된다.

## 기본 작업 흐름

모든 작업은 `touch` 명령어를 통해서 파일을 만드는 것으로 대체

### 1.`add`

``` bash
$ git add __디렉토리__
$ git add a.txt  #특정 파일
$ git add my_folder #특정 폴더
$ git add a.txt b.txt #특정 파일들
$ git add . # 현재 디렉토리(하위 디렉토리 포함)
```

* 커밋 대상 파일 목록에 추가한다.
* working directory의 변경사항을 staging area 상태로 변경시킨다.

## add 이전

``` bash
$ touch new.txt
$ git status

On branch master

No commits yet
# tracking x 파일들
# git으로 관리된 적이 없는 파일(새로 만든 파일 등)
Untracked files:
	# 포함시키기 위해서는 git add 명령어를 사용..
	# 커밋이 될 것
	# => 두번째(Staging area)에 담기 위해서..
  (use "git add <file>..." to include in what will be committed)
        new.txt

# SA x,
# WD o (working directory)
nothing added to commit but untracked files present (use "git add" to track)
```

## add 이후

``` bash
$ git add .
$ git status
On branch master

No commits yet
# 변경사항들.. 커밋될
# Staging area o
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   new.txt
```

### 2.`commit`

``` bash
$ git commit -m 'new.txt'
[master (root-commit) 81a8821] new.txt
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 new.txt
```

* `commit` 지금 파일 상태를 스냅샷
* 커밋 메세지는 코드 변경사항(이력/버전/커밋)을 충분히 잘 나타낼 수 있도록 작성한다.
* 아래의 명령어를 통해서 지금까지 기록된 커밋을 확인할 수 있다.

## log

``` bash
$ git log
commit 81a882144d0b0e2267aa7e1032e696491172ddf8 (HEAD -> master)
Author: qhillz <qhillz@naver.com>
Date:   Tue Mar 16 15:08:00 2021 +0900

    new.txt
$ git log --oneline
81a8821 (HEAD -> master) new.txt
$ git log -1  //최근 몇개를 볼 수 있다. 1개 2개 3개 
commit 81a882144d0b0e2267aa7e1032e696491172ddf8 (HEAD -> master)
Author: qhillz <qhillz@naver.com>
Date:   Tue Mar 16 15:08:00 2021 +0900

    new.txt
$git log --oneline -1
81a8821 (HEAD -> master) new.txt
```

## 원격저장소 기초 활용

## 준비

* github에 비어있는 저장소(repository)를 만든다.

# 기본 명령어

## 원격저장소 설정

``` bash 
$ git remote add origin __url___
#예시
$ git remote add origin https://github.com/qhillz/...
```

* 깃, 원격저장소(remote)를 추가해(add) 오리진이라는 이름으로 URL!
* 설정된 원격저장소를 인하기 위해서는 아래의 명령어를 활용한다.

~~~ bash
$ git remote -v
~~~

## push

``` bash 
$ git push origin master
```

## 설정

~~~ bash 
$ git config --global user.name '이름'
$ git config --global user.email '이메일주소'
커밋을 남기는 사람에 대한 정보(이메일, 이름)을 설정함.
~~~

* github 이메일주소와 동일하게 지정하면, 커밋 기록이 github 계정과 연동되어 표기 (예 - 잔디밭)
* 주의! 이 설정과 github 접근 권한(예-push)과는 전혀 상관 없음
  * 윈도우 - 자격 증명 관리자
  * 맥 - 키체인 접근


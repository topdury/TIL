## git - Intermediate





## branch

### 브랜치 생성하기(`git branch <name>`)'

### 브랜치 확인하기(`git branch`)

### 브랜치 확인하기(HEAD 움직이기`git switch <name>`)

=`check out <name>`



## 브랜치 생성 전환 한번에 하기

```
$ git switch -C <name>
=$ git checkout -B <name>
```

### 브랜치 삭제하기(`git branch -d <name>`)

### 브랜치 합병하기(`git branch merge <subname>`)

**항상 master에서 다른 브랜치를 병합한다.**

## remote(github에 main 저장소와 연동)

```
$ git remote add (origin) <저장주소>
$ git remote -v 
topdury 저장주소 나옴
```

## PUSH(`git push origin master`)

**master는 내 pc 에 master 를 말하고(언제든 branch name으로 할수 있음) origin은(내 github 메인 저장소 이름)**

## Pull(`git pull origin master`)

**master는 내 pc 에 master 를 말하고(언제든 branch name으로 할수 있음) origin은(내 github 메인 저장소 이름)**

## Clone(처음으로 github에서 repo를 가져올때)

```
$ git clone <URL>
협업이나 새로운 환경에서 작업을 시작할 때 필수적으로 해야함(자신이 repo주체라면 하면 안됨 중복 repo로 오류남)
```

## Vim(`$ vim`)

터미널에서 수정해야할 떄 i(insert)->ESC(끝내기)->:wq(저장,나가기)

:q! 강제나가기

## Ingnore

```
비쥬얼 코드 다운이 우선

파일 일 경우
$touch .gitignore
ingnore할 log 파일을 서치하는 사이트
http://gitignore.io 
쓰고 있는 프로그래밍 tool이름을 넣고 enter 긁어서 붙여넣기
```

## Cached(untrack으로 변환) 

`$ git add <name>`을 한 파일을 untrack 상태로 변환

```
파일
$ git rm --cached <name>

폴더
$ git rm -r --cached <폴더명>
```


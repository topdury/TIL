

# Github 특강

## git과 github

git=소스 , github=백업목적(cloud)

## git 설치

1. git-scm.com에서 다운로드
2. 계속 next로 설치

## git 사용법

### 최소 설정

로컬c->사용자->내계정

처음 git을 설치하면 사용자의 이름을 적어준다. 이는 앞으로 일어나는 commit에 서명을 하기 위해서 필요하다.

```
$  git config --global user.name "<당신의 이름>"

$ git config -- global user.email "<당신의>@<이메일>"
```

잘 설정되었나 확인하려면

```
$ git config user.name 
이름 출력

$ git config user.email
이메일 출력
```



### 상태점검

```
$ git status
```



### 초기화 

초기화는 `git init`을 통해 진행한다.

```
$ git init
빈 디렉토리(폴더)를 git 저장소(repo)로 초기화 한다.
$ ls -a 
전부 보여줌(.git을 확인할수 있음)
$ rm -rf.git 
git 없애기
```



### add하기

수정 파일이나 untrack파일을 stage에 올리는 것

``` 
$ git add 파일명

$ git add . or -A
변경사항이 있는 것을 모두 stage에 올림
```

### commit하기

예를 들어 사진을 찍어서 기록을 남기는 단계

```
$ git commit -m '<원하는이름>'
$ git commit 시 메모로 들어가짐 

나오는법
ECS연타->:q!
```

### Log보기 

사진첩을 보는 단계로 기록을 보여준다.

```
$ git log
```

### 꿀명령어

| 명령어                  | 설명                       |
| ----------------------- | -------------------------- |
| `$ mkdir 'name'`        | 폴더만들기                 |
| `$ touch 'name.확장자'` | 문서 만들기                |
| `$ cd ..`               | 위로가기                   |
| `$ ls`                  | list 보기                  |
| `$ git restore`         | stage에 올린 것을 다시내림 |








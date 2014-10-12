
Gitolite는 간단하게 git server를 구성할 수 있는 툴이다.

git-server에 git repository를 구성하고, 프로젝트와 사용자를 추가해본다.

**Assumption:**

 - git 서버: git-server
 - 관리자 계정 : tsyoum@pc

## 설치하기

@ git-server

    git-server tsyoum$ sudo adduser git
    git-server tsyoum$ su git
    git-server git$ mkdir bin (이후 PATH에 bin 추가)

gitolite 를 다운로드 받는다.

    git-server git$ git clone git://github.com/sitaramc/gitolite
    git-server git$ gitolite/install -ln

미리 복사해 둔 관리 계정의 RSA public key를 관리자 계정으로 추가한다.

    git-server git$ gitolite setup -pk tsyoum.pub

이것으로 설치 끝.

다음은 관리자 pc에서 관리용 git repository를 생성한다.

@PC

    pc tsyoum$ git clone git@git-server:gitolite-admin.git


## 새 프로젝트 시작하기

foo 라는 이름의 project를 추가해보자.

conf/gitolite.conf에 다음 내용을 추가하고 push 해주면 끝.

    pc tsyoum$ cd gitolite-admin

    pc tsyoum$ vi conf/gitolite.conf

repo foo

   RW+ = tsyoum


## foo 프로젝트에 사용자 (robin) 추가하기

1. conf/gitolite.conf에 robin 추가

repo foo

     RW += tsyoum robin

2. public key 추가

    $ cp robin.pub keydir

이제 gitolite.conf와 robin.pub를 add/commit/push 하면 된다.


## 기존 git project를 추가하기

bar라는 기존 git 프로젝트를 서버에 추가해본다.

먼저 bar project를 gitolite에 등록한 뒤에, local의 bar repository를 다음과 같이 서버에 추가한다.

    $ cd bar

    $ git push --all git@git-server:bar

    $ git push --tags git@git-server:bar

그리고 remote repo를 origin으로 등록한다.

    $ git remote add origin git@git-server:bar



## 참고한 페이지

[http://sitaramc.github.com/gitolite/qi.html](http://sitaramc.github.com/gitolite/qi.html)

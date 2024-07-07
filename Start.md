# Git setup

## 1. 사용자 계정
```
      #Create Account
      git config --global user.name " Your name"  
      git config --global user.email "Yourmail@mail.com"

      #User Info
      git config --list
```

## 2. Linux Commands
```
  1. pwd # Current place
  2. ls  # list of file(s) and folder(s) at the current place
  3. ls -la # hidden info and detail info
  4. ls -t # rearranged by time
  5. cd ~ # Go back to home directory
```

## 3. Folder 초기화
```
git init # initialize the current folder
```

## 4. 개념 - Local의 경우
### 3가지 단계로 파일을 저장하고 관리 한다.
### 1) Working Tree (Working Directory): 작업을 하고 있는 문서나 코드가 있는 곳  
### 2) Stage : Git에 저장하기 전에 임시로 올려 놓은 장소 .git/index에 저장 됨  
```
git add "File" # stage에 file을 올린다.
git status # 상태 확인 chagned to be committed가 된다.
```
### 3) Repository : Stage에 대기하고 있는 파일을 최종적으로 저장하는 장소
```
git commit -m "message" # message라는 주석을 달고 stage에 있는 파일을 저장소 저장

git commit -am "message2" # 한 번 이상 commit한 파일에 대해서는 add와 commit을 한 번에 실챙

```

## 5. 저장소 상태 관련

### 1) git log 명령어를 통해  저장소 정보 확인
```
git log #저장소에 저장 된 버전을 확인 할 때 사용
$ git log
commit 1ee8e6ef8427905920c0e2c04dca995814988645 (HEAD -> master)
Author: DooHub <djmen76@naver.com>
Date:   Thu Jun 27 22:08:59 2024 +0900

```
### 2) git diff 바로 commit한 버전과 이전 버전 차이 확인

## 6.작업 되돌리기
### 1) Working Tree에서 되돌리기
```
git checkout -- filename.extension

```
### 2) State에서 되돌리기
```
git reset HEAD filename.extension
```

### 3) Repository에서 되될리기
```
git reset HEAD^ #최신 것 취소 하기

git reset --hard commit ID # 해당 commit ID 이후 부분은 삭제

git revert commit ID # 해당 commit ID 이후 부분은 삭제하지 않고 돌아 감
```


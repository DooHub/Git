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
### 3) Repository : Stage에 대기하고 있는 파일을 최종적으로 저장하는 장소

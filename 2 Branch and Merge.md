# Condition : MCU BSW개발 시 하기 상태를 고려해서 진행
### Base(master) : ADS compile 및 EBtresos가 실행 될 수 초기 단계
### SPI(spi) : SPI 통신 Module. Base 위에서 동작
### ADC(adc) : ADC Module. Base 위에서 동작
### Release(release) : SPI와 ADC가 통합 된 SW

# 1. Command
### 어느 단계에서 그 부분을 포함한 다른 단계로 나갈 때 사용 - SPI,ADC, Release
## 1) git branch "folder name"
```
$ git branch spi #branch 만들기
$ git branch #branch 목록 및 현 위치 확인
* master
  spi
```
## 2) git checkout "branch folder name"
```
/MCU (master)
$ git checkout spi
Switched to branch 'spi'

/MCU (spi)
$ git branch
  master
* spi
```

## 3) git log 관련 option  
### --oneline : 한줄양식으로 간략히 보여줌  
### --branches : branch 관계를 표시해 줌
### --graph : branch 관계를 화살표로 표시해 줌
```
/MCU (adc)
$ git log --oneline --branches --graph
* a303e23 (HEAD -> adc) adc mdule 1
| * e57cac4 (spi) spi module 1
|/
* d5f4572 (master) Base
```
## 4)branch간 차이점 알아보기
### git log 기준branch..비교branch : 기준 branch에는 없는 비교branch내용 표시
```
/MCU (adc)
$ git log adc..spi
commit e57cac4d8d8c8e72075bd1af13276e581e76b1e8 (spi)
Author: ** <d**@naver.com>
Date:   Sun Jul 7 19:57:16 2024 +0900

    spi module 1

/MCU (adc)
$ git log spi..adc
commit a303e231df301d74cb3bb37e6a62c465a8aa5642 (HEAD -> adc)
Author: ** <d**@naver.com>
Date:   Sun Jul 7 19:58:52 2024 +0900

    adc mdule 1
```
## 5)merge 방법
### base가 되는 branch로 checkout한 후에 merge "merge 하려는 branch name"
### release branch에 spi와 adc를 merge 하는 경우
```
/MCU (master)
$ git checkout release
Switched to branch 'release'

/MCU (release)
$ git merge spi
Updating d5f4572..e57cac4
Fast-forward
 spi.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 spi.txt

/MCU (release)
$ git merge adc
Merge made by the 'ort' strategy.
 adc.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 adc.txt

/MCU (release)
$ ls -la
total 7
drwxr-xr-x 1 dusti 197609  0 Jul  7 20:10 ./
drwxr-xr-x 1 dusti 197609  0 Jul  7 19:46 ../
drwxr-xr-x 1 dusti 197609  0 Jul  7 20:10 .git/
-rw-r--r-- 1 dusti 197609 10 Jul  7 19:46 Base.txt
-rw-r--r-- 1 dusti 197609 14 Jul  7 20:10 adc.txt
-rw-r--r-- 1 dusti 197609 14 Jul  7 20:10 spi.txt

/MCU (release)
$ git status
On branch release
nothing to commit, working tree clean

/MCU (release)
$ git commit -m "spi adc merge"
On branch release
nothing to commit, working tree clean

/MCU (release)
$ git status
On branch release
nothing to commit, working tree clean

/MCU (release)
$ git log
commit 410fc3aa421249fa13915095cf1023975500754a (HEAD -> release)
Merge: e57cac4 a303e23
Author: ** <d**@naver.com>
Date:   Sun Jul 7 20:10:15 2024 +0900

    Merge branch 'adc' into release

commit a303e231df301d74cb3bb37e6a62c465a8aa5642 (adc)
Author: ** <d**@naver.com>
Date:   Sun Jul 7 19:58:52 2024 +0900

    adc mdule 1

commit e57cac4d8d8c8e72075bd1af13276e581e76b1e8 (spi)
Author: ** <d**@naver.com>
Date:   Sun Jul 7 19:57:16 2024 +0900

    spi module 1

commit d5f4572fbca157da2edef2e6053dcf8842ec8588 (master)
Author: ** <d**@naver.com>
Date:   Sun Jul 7 19:47:20 2024 +0900

    Base
```
# 2. 기타 내용
### 1) 같은 자리에 다른 branch에서 작성한 파일을 merge할 때 처리 방법  
### 해당 파일 내 '<<<<<<< HEAD'와 '>>>>>> branch name'과 '============' 을 삭제(이 부분이 중복 되는 위치) 후 commit하여 처리

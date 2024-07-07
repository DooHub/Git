# Condition : MCU BSW개발 시 하기 상태를 고려해서 진행
### Base(master) : ADS compile 및 EBtresos가 실행 될 수 초기 단계
### SPI(spi) : SPI 통신 Module. Base 위에서 동작
### ADC(adc) : ADC Module. Base 위에서 동작
### Release : SPI와 ADC가 통합 된 SW

# 1. Command
### 어느 단계에서 그 부분을 포함한 다른 단계로 나갈 때 사용 - SPI,ADC, Release
# 1) git branch "folder name"
```
$ git branch spi #branch 만들기
$ git branch #branch 목록 및 현 위치 확인
* master
  spi
```
# 2) git checkout "branch folder name"
```
dusti@DESKTOP-J62GKVR MINGW64 /d/git_test/MCU (master)
$ git checkout spi
Switched to branch 'spi'

dusti@DESKTOP-J62GKVR MINGW64 /d/git_test/MCU (spi)
$ git branch
  master
* spi
```



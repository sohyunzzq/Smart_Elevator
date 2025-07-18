# 💡 스마트 엘리베이터  
![image](https://github.com/user-attachments/assets/1becd7b6-6b6c-469f-981d-2a195660fefb)

---

## 📌 개요  

- 스마트 엘리베이터는 불필요한 문열림을 줄이고, 카메라와 로드셀 센서(무게 센서)를 통해 엘리베이터 내외부의 이용자 및 대기자의 정보를 제공함으로써 이용 가능성을 예측할 수 있도록 한다. 이를 통해 이용자의 시간과, 엘리베이터의 불필요한 에너지 낭비를 감소시키는 것을 목표로 한다.
- 백화점, 회사, 아파트, 고층 건물 등 엘리베이터 이용이 빈번한 환경에서의 활용이 기대된다. 또한 탑승 가능 인원을 무게 기준으로 예측하기 때문에 화물용보다는 승객용 엘리베이터에 더욱 적합할 것으로 보인다.

---

## 🔍 개발 배경  

- 엘리베이터를 타다 보면, 중간에 멈췄지만 아무도 없는 층에서 문이 열리거나, 버튼을 눌렀지만 엘리베이터가 금방 오지 않아 서둘러 계단을 이용한 적이 있을 것이다. 또한, 기껏 기다렸지만 엘리베이터가 만원이라 타지 못하는 경우도 겪어봤을 것이다.  
- 우리는 이러한 사람들의 실생활 속 불편함과 시간 낭비 및 엘리베이터의 에너지 소비 등 문제를 줄이기 위해, 불필요한 정차를 방지하고, 실시간 정보로 사용자에게 도움을 주는 스마트 엘리베이터를 설계해보았다.

---

## 🛠 사용 기술 및 개발 환경  
- 언어: Python (tkinter, 영상처리)  
- 하드웨어: Raspberry Pi 4 Model B  
- 툴: Thonny (Raspberry Pi 기본 Python IDE), VNC Viewer, Putty  

---

## 🧱 사용 부품  
- Raspberry Pi 4 Model B 2대
- Raspberry Pi Camera 4대
- 멀티 카메라 보드 (Multi Board)
- 무게추
- 로드셀 센서
- 하드보드지 (엘리베이터 모형)
- LCD 디스플레이
- 스위치 10개
- LED 4개

---

## ⚙️ 환경 설정 방법  
### HW
- 연결한 GPIO 핀에 따라 weight.py의 핀 번호 변수 수정
- 무게추(혹은 다른 도구) 하나당 평균값과 허용 오차 수정 (default: 50g)

---

## 🔧 주요 기능

### 🛗 엘리베이터 동작

- 엘리베이터 내부 1~4층 버튼과 각 층의 상/하향 버튼을 눌러 목적지 생성
- 입력된 목적지에 따라 엘리베이터가 GUI 상에서 이동
- 현재 층은 LCD와 LED로 실시간으로 표시

### ⚖️ 엘리베이터 내부 무게 감지

- 무게추를 올려 탑승 시뮬레이션 시행
- 로드셀 센서로 무게를 측정해 현재 층, 혼잡도, 수용 가능 인원을 LCD에 표시 (전원 5명)
- 로드셀 측정 결과 인원이 1명 이상이면 내부 LED를 켜고, 없으면 끔

| 수용 가능 인원 | 표시 문구    |
|----------------|--------------|
| 5~4명          | pleasant     |
| 3명            | normal       |
| 2~1명          | congest      |
| 0명            | full         |

### 🎥 카메라 인식

- 각 층의 카메라가 대기자를 인식  
- 사람이 없으면 해당 층의 외부 버튼 자동 해제  
- 촬영된 이미지를 화면에 표시해, 사용자가 엘리베이터를 기다릴지 판단할 수 있도록 지원  
<img width="385" height="370" alt="image" src="https://github.com/user-attachments/assets/23c9ee7f-6e4b-4822-9e3b-6540ea27e93b" />  

> 동서남북 방향으로 4개의 카메라를 설치하고 멀티 카메라 모듈로 연결해 사람을 인식한다.  

---

## 🔌 하드웨어 구성 및 회로도  
![image](https://github.com/user-attachments/assets/0c38af7f-fed0-4bc4-8aee-ad969b5a84c4)  
> 위와 같이, 엘리베이터 동작용 Raspberry Pi 1대, 무게 감지용 Raspberry Pi 1대 따로 두었다.

![image](https://github.com/user-attachments/assets/accd51c4-7596-4958-923d-59503172b3b9)

---

## 🧰 제작 과정  
- 하드보드지로 전체 틀 제작
- LCD, LED, 로드셀 센서 각각 부착
- 엘리베이터 내부와, 외부 각 층마다의 버튼을 하드보드지에 부착 후 층수 표시 
- 센서들의 점퍼선은 엘리베이터 뒤로 빼내 브레드보드와 연결
- 하드보드지로 지지대 제작 후, 4개의 카메라가 각 방면을 가리키도록 부착

--- 

## 📷 시연 영상 및 결과 화면  
<img width="270" height="270" alt="image" src="https://github.com/user-attachments/assets/ea904192-f1f8-4b46-8ec7-f321dc776978" />
<img width="270" height="270" alt="image" src="https://github.com/user-attachments/assets/19196569-53e9-404a-8ad5-c031ec1647d2" />
<img width="270" height="270" alt="image" src="https://github.com/user-attachments/assets/40afbad3-56a7-4ed4-a4db-bd5b366a2017" />  

> 로드셀 센서가 인식하는 무게에 따라, 현재 몇 명이 더 탈 수 있고(5명 정원), 내부 혼잡도가 어떤지 LCD에 출력된다.



---

## 📁 디렉터리 구조

```
├── docs/
│   └── dev-log.md    
├── README.md
├── elevator.py
└── weight.py
```

---

## 🚀 실행 방법
1. Arduino 연결 후 brai.ino 업로드 (시리얼 모니터가 열려 있으면 실행이 되지 않으므로 꼭 닫아주기)
2. PyCharm에서 user.py 실행 후 문자열 입력
3. 솔레노이드 작동 확인
 
---

## 💭 한계  
- 총 4층의 공간을 실시간 영상으로 송출하려고 하였으나, Raspberry Pi 설정에서 legacy camera 권한을 허용하자 화면이 블랙아웃되었고 VNC를 사용할 수 없었음. tensorflow를 활용하려면 GUI가 필요했기 때문에 tensorflow 대신 libcamera를 활용하기로 결정함.
- multi board를 활용해 카메라 총 4대를 사용하려고 하였지만, multi board는 동시 동작이 아닌 순차 동작을 지원했기 때문에 각 층을 순서대로 찍고 그 사진에서 얼굴 인식을 진행하였음. 
- 하드웨어 안 예쁨  
- 엘리베이터 알고리즘 완벽 구현 못함
- 층수를 유연하게 조절하지 못함 (하드웨어 같은 거)

---

## 📚 참고 자료
- pin map

사진

- 표

사진

# BME_bachelor_thesis (2024.07~2024.12)

&nbsp;

## 🧠 Hospital system with self-driving Ambulance using Unity

&nbsp;

## 🔗 출처 및 라이선스
### 1. Autonomous Driving with Unity and BMW: 240 Million Virtual Kilometers -NICK DAVIS
 - https://unity.com/kr/blog/industry/bmw-automotive-lifecycle
### 2. Self-Driving Ambulance for Emergency Application -Mainak Kumar Das
- https://ieeexplore.ieee.org/document/9614822

     
&nbsp;

## 📑 목차

1. [📌 프로젝트 개요](#1--프로젝트-개요)  
2. [🔧 구성 요소](#2--구성-요소)  
3. [💻 사용 기술](#3--사용-기술)  
4. [🧭 동작 흐름 요약](#4--동작-흐름-요약)  
5. [💻 코드 실행 방법](#5--코드-실행-방법)  
6. [📷 시연 영상/이미지](#6--시연-영상--이미지)  
7. [🌟 기대 효과/ 한계점 및 개선점](#7--기대-효과)  

   
&nbsp;
## 1. 📌 프로젝트 개요

효율적인 응급 대응은 특히 전문 진료가 필요한 환자의 경우 생명을 구하는 데 결정적인 역할을 합니다.  
그러나 기존의 앰뷸런스 시스템은 다음과 같은 문제를 겪고 있습니다:

- **전문 병원의 제한된 가용성**
- **가장 가까운 앰뷸런스를 신속히 배차하는 어려움**
- **복잡한 도심 환경에서의 이동 지연**

이러한 문제를 해결하기 위해, 본 프로젝트는  
**실시간 환자 우선순위 판단과 자동 배차 기능을 결합한 자율주행 앰뷸런스 시스템**을 개발하여  
응급 이송 시간을 최적화하는 것을 목표로 합니다.
  
&nbsp;

## 2. 🎯 기획 의도

기존의 수동적인 앰뷸런스 운영 방식은 교통 체증, 병원 혼잡도, 인력 부족 등 다양한 변수로 인해  
환자 이송 지연이라는 치명적인 문제를 발생시킵니다.  

본 시스템은 다음과 같은 점에 중점을 둡니다:

- **카메라 및 OpenCV 기반 차선 인식**으로 멀티 차선 도로를 자율적으로 주행  
- **Unity의 Raycast** 기능을 이용하여 주변 차량을 감지하고, 차선 변경 및 속도 조절 자동 수행  
- 환자 상태에 따른 **실시간 우선순위 판단과 자동 경로 설정** 기능을 결합  
- **병원의 거리, 혼잡도, 전문 진료 가능 여부**를 고려하여 가장 적합한 병원으로 자동 이송

이를 통해 응급 환자의 생존 가능성을 높이고, 전체 응급 시스템의 효율을 향상시킬 수 있습니다.
  
&nbsp;

## 3. 🏭 기존 기술의 활용과 확장 가능성

본 프로젝트는 다양한 기술 요소를 유기적으로 결합하여 다음과 같은 장점을 가집니다:

- Unity 시뮬레이터를 활용한 현실적인 도로 환경 구현  
- 카메라와 OpenCV 기반의 차선 탐지 알고리즘으로 자율주행 구현  
- Raycast 기반 충돌 회피 로직으로 안전한 차량 간 거리 유지 및 회피 가능  
- 병원 데이터와 연동된 실시간 판단 시스템으로 경로 최적화 및 병원 자동 연결  

이 시스템은 향후 다음과 같은 영역으로 확장 가능합니다:

- 실제 자율주행 구급차량 시스템에의 적용
- 재난 대응용 드론 또는 로봇 응급 구조 시스템과 연계
- 스마트 시티 인프라와 연동한 병원-도로 네트워크 구축
- 고령자·장애인을 위한 비대면 응급 호출 플랫폼으로 발전

&nbsp;
## 2. 🔧 구성 요소

| 구성 요소            | 설명                                                                 | 이미지 |
|---------------------|----------------------------------------------------------------------|--------|
| **Arduino Nano 33 BLE Sense** | EOG 센서로부터 신호를 받아 실시간으로 시선 방향을 분석하고, 딥러닝 모델을 통해 판단된 결과에 따라 로봇팔을 제어함. | <img width="300" src="https://github.com/user-attachments/assets/5a5c921e-9021-4990-8892-2aa33eaebafc" /> |
| **PSL-iEOG2 EOG 센서**        | 안구 전위(Electrooculogram)를 감지하여 눈의 좌우 움직임과 깜빡임 등을 아날로그 신호로 출력함.           | <img width="300" src="https://github.com/user-attachments/assets/dc2073be-53a0-4884-b0e6-b9ad2de862f3" /> |
| **서보 모터 (SG90 / MG995)** | 로봇팔 관절을 구동하여 시선 방향에 따라 원하는 위치로 움직임을 수행함. MG995는 힘이 필요한 부위, SG90은 가벼운 부위에 사용됨. | <img width="300" src="https://github.com/user-attachments/assets/97048b8f-518e-4930-895a-cad75dea3428" /> |
| **3D 프린터 로봇팔** | 실제 음식을 집을 수 있도록 설계된 로봇 팔 구조물. 3D 프린터로 출력하여 사용자 맞춤형 형태로 제작 가능.         | <img width="300" src="https://github.com/user-attachments/assets/2814adce-4669-40f8-b355-288e6d7c45f6" /> |

- PSL-iEOG2 : 168,960원
- arudino Nano 33 BLE : 59,900원
- TowerProM mg995 모터 4개 : 26000원
- SG-90 모터 2개 :２,800원
- AA*3 배터리팩 4개 : 4000원
- AA 배터리 5개 : 13500원
- 아두이노 우노 2개 :19800원
- 배터리 3구 홀더 2개 : 1980원
- breadboard 1개 : 800원
- arudino uno R3 : 26500원
- arudino nano : 29100원
- breadboard Jumper 18개 : 43200원

&nbsp;

## 3. 💻 사용 기술

| 기술 | 내용 |
|------|------|
| 💻 OS 및 환경 | Ubuntu 22.04, ROS2 Humble |
| 💬 사용 언어 | Python, DSR |
| 🔗 통신 미들웨어 | ROS2 (Publisher / Subscriber 기반 노드 통신) |
| 🧪 순응제어 | Doosan M0609 Force 센서를 활용한 충돌 감지 및 위치 파악 |
| 🧠 서브 제어 컨트롤러 | Raspberry Pi (로컬 ROS2 노드 실행 및 장치 제어) |
| 🎮 인터페이스 | 사용자 입력 기반 물품 선택 |
| 🖥 디스플레이/음성 | Raspberry Pi + LCD + 음성 출력 |

&nbsp;
## 4. 🧭 동작 흐름 요약

<img width="652" height="473" alt="image" src="https://github.com/user-attachments/assets/340626b4-d98d-4b9c-bfdc-103f4d0fc735" />

&nbsp;

### 📡 EOG 수집
EOG란 각막과 망막 간 전위를 측정 결과 발생하는 신호로 눈의 움직임을 기록할 때 주로 사용된다.  
피지오랩사의 PSL EOG 센서를 이용하여 안구전도를 측정하였고, 아두이노 나노와 연결하여 Arduino IDE 및 Serial SW를 통해 측정 결과를 확인하였다.

이번 논문에서는 눈의 좌우에 전극을 배치하여 horizontal한 EOG를 얻었다.  
전극은 총 3개로 양안의 좌우와 이마 중앙에 부착하여 전압차이를 각각 측정할 수 있다.

- PSL 센서는 2채널 신호를 제공 (아날로그, 디지털)  
- 이 중 아날로그 신호만 사용  
- 750V/V 증폭도  
- 60Hz notch filter 포함  
- 0.05Hz cutoff frequency의 high pass filter  
- 10Hz cutoff frequency의 low pass filter  
- 출력 전압: 0~3.3V

<img width="797" height="281" alt="image" src="https://github.com/user-attachments/assets/408c7b3e-a216-483f-af66-ad0f24a5c994" />

<img width="807" height="404" alt="image" src="https://github.com/user-attachments/assets/937b0241-c563-4d71-8d9b-f2b6f350d047" />

분석을 위해 먼저 데이터 전처리를 수행하였다.

- Sampling frequency를 125Hz로 downsampling  
- 평균 값 제거 및 scale 확대를 통해 데이터를 더 정확히 파악  
- 1초 간격으로 정면과 left (또는 right)를 바라봄  
- 2초 간격 (250 sample) 으로 EOG를 분리하여 확인

결과를 보면 왼쪽과 오른쪽을 바라봤을 때의 EOG 파형은 차이가 있었다.  
- 왼쪽 → 중앙에서 아래로 떨어지는 파형  
- 오른쪽 → 위로 튀는 파형  

전체 데이터 셋에서 확인해보면 아래와 같은 파형이다.

> 특히 현재 측정 중인 EOG는 안구 움직임의 변화를 측정하기 때문에  
> 왼쪽과 오른쪽 EOG 간의 데이터 절대값 크기는 큰 차이가 없었으며,  
> threshold로 단순 분류하기엔 한계가 있었다.

<img width="800" height="233" alt="image" src="https://github.com/user-attachments/assets/099fff83-1609-4978-b938-a644da3eaa8b" />

&nbsp;

### 🔀 기울기 기반 분석

처음 방향 변화가 일어난 순간에만 EOG 변화의 기울기가 다른 것을 확인하였다.  
따라서 **안구 움직임 변화 직후 5초간의 EOG 데이터를 수집하고, 미분값으로 데이터셋을 구성**하였다.

<img width="800" height="249" alt="image" src="https://github.com/user-attachments/assets/6ff94c7b-98b6-4777-b3ae-cfd5dbbab40b" />

- 번갈아가며 30도, 90도 시선 전환 실험  
- 수치적으로 큰 차이는 없음  
→ 왼쪽, 오른쪽, 가운데만 분류한 후 **횟수로 각도 조절**

&nbsp;

### 🤖 모델 제작

- 각 데이터셋을 `SAMPLES_PER_EOG` 값인 5개 샘플로 나눠 데이터프레임에 저장  
- 각각 1차원 배열로 변환 후 `inputs` 리스트에 저장 

<img width="700" height="159" alt="image" src="https://github.com/user-attachments/assets/cd734c30-e586-48d6-a6b2-b6d0f463d68a" />

- 해당 세그먼트가 나타내는 눈동자 움직임 유형: `left`, `right`, `center`  
- 이를 one-hot encoding하여 `outputs` 리스트에 저장

&nbsp;

### 🤖 모델 비교 및 선정

EOG 방향 분류를 위한 3가지 모델을 구현하고 성능 비교 후 최종 모델 선정

- CNN: 정확도 80.7%  
- SVM: 정확도 88.8%  
- **LSTM: 정확도 92.5% → 최종 선택**

<img width="700" height="300" alt="image" src="https://github.com/user-attachments/assets/e5efd2e9-1446-4b7b-b44f-40b92dc432a2" />

<img width="1059" height="598" alt="image" src="https://github.com/user-attachments/assets/974decef-c945-4a01-bc82-730f28b3d2e4" />

&nbsp;

### 🛠️ 로봇팔 3D 프린팅 및 조립

- 복잡하고 정밀한 작업을 수행 가능한 6 DOF 로봇팔을 설계  
- 3D 모델링 진행 후 부품 제작 및 조립  
- 모터 구성:  
  - MG995 (기저 회전, 어깨 2개, 팔꿈치)  
  - SG90 (팔목, 집게)

<img width="800" height="253" alt="image" src="https://github.com/user-attachments/assets/b0077c95-b36c-4cac-a398-0931d86e590d" />

&nbsp;

### 🔌 회로 구성

- 각 모터 전선을 연장 후 Arduino 보드 핀 번호에 맞게 연결  
- 모터에 강한 힘을 주기 위해 5V 파워 서플라이를 별도 연결  
- 전력 손실 최소화를 위해 짧은 점프선 사용

&nbsp;

### 💻 Arduino 코드 구성

- 사용 보드: **Arduino Nano 33 BLE Sense**  
- Arduino 코드로 서보모터 제어 → 로봇팔 동작 구현
- 각 모터의 핀과 각도 제어를 통해 **정확한 집기 동작** 구현

<img width="1119" height="759" alt="image" src="https://github.com/user-attachments/assets/0052be4e-ef41-47a7-84c9-b2604e01437f" />

<img width="1124" height="723" alt="image" src="https://github.com/user-attachments/assets/58e24a3b-5bac-46b5-af82-9e61803bb4fe" />

&nbsp;

### 🔁 방향 전환 로직

- EOG 센서를 이용해 방향 전환 감지  
- 상태 머신 설계(State Machine)로 방향에 따라 로봇팔 동작 분기

<img width="1124" height="629" alt="image" src="https://github.com/user-attachments/assets/6f8ef34f-51cc-4cb8-92f0-d392a9d9a9fc" />

<img width="440" height="158" alt="image" src="https://github.com/user-attachments/assets/58844b15-6e3e-4815-a592-17cf558783b1" />

<img width="883" height="399" alt="image" src="https://github.com/user-attachments/assets/1d651cbf-0edd-45bf-aee6-c6f938ea0c28" />

&nbsp;

## ✅ 결과

<img width="857" height="341" alt="image" src="https://github.com/user-attachments/assets/3a3af50d-4ca5-4de7-8538-c315d31d9a54" />

- 사용자의 눈 움직임만으로 로봇팔이 정확한 방향 전환 및 집기 동작 성공  
- LSTM 기반 EOG 분류 모델과 로봇팔 동작 시스템의 실시간 연동 가능성 확인

&nbsp;


## 5. 💻 코드 실행 방법

### 🤖 EogDeepLearning-Robot
- 코드: [`eog_deeplearning`](./Arduino/Arduino/eog_deeplearning/eog_deeplearning-DESKTOP-O965BML.ino)


&nbsp;



## 6. 📷 시연 영상 / 이미지
### 경희대학교 전자공학과 졸업논문 발표
<img width="670" height="481" alt="image" src="https://github.com/user-attachments/assets/ee818f96-756f-4eaf-9bdc-710e653cd323" />

&nbsp;

### 경희대학교 캡스톤 디자인 대회 최우수상
![캡스톤디자인대회전체사진](https://github.com/user-attachments/assets/d9fc142f-a1ec-436a-888b-d0d8fbc1dbe4)

![캡스톤디자인대회최우수상](https://github.com/user-attachments/assets/9c34a8d0-3c7f-4ca7-8bd4-0bce211a80c4)

&nbsp;

> https://youtu.be/0Lg0ZxRh0jA

&nbsp;
## 7. 🌟 기대 효과
EOG 센서는 빠른 반응 속도를 제공해 사용자의 의도를 **즉시 반영**할 수 있습니다.  
이를 통해 로봇팔의 **실시간 제어**가 가능해져 시스템의 효율성이 높아집니다.

또한 피부에 부착하는 방식이므로, 수술이나 복잡한 설치 과정 없이 **몸이 불편한 사용자도 간편하게 사용 가능**하여 **접근성과 안전성**이 매우 뛰어납니다.  

> 이를 활용해 산업, 의료, 서비스 등 다양한 분야로 **응용 범위를 확장**할 수 있습니다.

&nbsp;

### 🛠️ 활용 방안

- **보조기기**: 신체 일부가 불편한 사람들을 위한 **일상 동작 지원 장치**로 사용 가능  
- **재활치료**: 사용자의 자율성 증진을 통해 **회복을 돕는 치료 보조 장치**로 활용  
- **산업 분야**: 정밀 제어가 필요한 제조 환경 등에서 자동화 도구로 활용  
- **서비스 분야**: 음식 및 음료 서빙 등 **비접촉 자동화 서비스 시스템**에 적용 가능  
  (예: 카페, 레스토랑 등)

&nbsp;
 
### 🔍 결론 및 제언

EOG 센서를 이용한 로봇팔 제어 기술은 **생체 신호 기반의 정밀하고 신속한 제어**를 가능하게 합니다.  
비침습적 인터페이스를 통해 **사용자의 편의성과 안전성을 보장**하며, 다양한 환경과 작업 조건에서 **효율적으로 적용**될 수 있습니다.

> 여러 분야에서의 활용 가능성을 고려할 때, 이 기술은 인간의 생활을 더욱 **풍요롭게** 하고,  
> 새로운 **혁신을 이끌어 낼 수 있는 잠재력**을 가지고 있습니다.


### 📌 **향후 제언**
- 지속적인 연구 및 개발  
- 사용자 중심의 기술 설계  
- **윤리적 고려**와 **사회적 수용성** 확보

> 이를 통해 EOG 기반 로봇 제어 기술이 더욱 발전하여  
> 우리의 삶에 **긍정적인 영향**을 미치기를 기대합니다.

&nbsp;
## 🙌 팀원

-윤하연, 정서윤, 안병호 



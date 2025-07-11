# 🚛 스마트 AGV 물류 프로젝트 (Autonomous Guided Vehicle)

## 📋 프로젝트 개요
AI 기반 라인트레이싱과 색상 인식을 활용한 자율주행 물류 로봇 시스템입니다. IoT 센서와 웹 대시보드를 통해 실시간 모니터링이 가능한 스마트 물류 솔루션을 제공합니다.

![프로젝트 개요](https://github.com/user-attachments/assets/a81bcc40-b92a-44ff-80de-60cac8f67efa)

---

## 👥 팀원 소개

<div align="center">
  <img width="512" height="343" alt="팀원 소개" src="https://github.com/user-attachments/assets/fdd4f5bd-a740-4ab5-af82-584929d0ac1e" />
</div>

---

## 🎬 시연 영상

https://github.com/user-attachments/assets/625fcdb4-eb43-40b4-9f03-52f72d30219d

---

## 🎯 프로젝트 기획

![프로젝트 기획](https://github.com/user-attachments/assets/acf0ea19-23aa-4bea-9aa0-a033f29829d7)

### 주요 목표
- **자율주행**: AI 기반 라인트레이싱으로 정확한 경로 추종
- **색상 인식**: 목적지 및 화물 구분을 위한 컴퓨터 비전 구현
- **IoT 연동**: 실시간 센서 데이터 수집 및 전송
- **웹 대시보드**: 직관적인 모니터링 및 제어 인터페이스

---

## 🛠️ 기술 스택

### Hardware
- **MCU**: Jetson Nano/Raspberry Pi5
- **센서**: Camera
- **Vehicle** : JETANK

### Software
- **AI/ML**: OpenCV, PyTorch
- **Frontend**: Vue.js, QT Framework
- **Backend**: Python
- **Database**: Firebase firestore
- **Network**: MQTT, TCP/IP Socket

---

## 📊 나의 결과물

### 1. 🤖 AI 라인트레이싱
컴퓨터 비전과 머신러닝을 활용한 정밀한 라인 추종 시스템을 구현했습니다.

![AI 라인트레이싱](https://github.com/user-attachments/assets/a4666c8f-7e89-4762-b311-dca89087232a)

**주요 기능:**
- 실시간 라인 검출 및 추종
  - ResNet 딥러닝 모델을 Fine-tuning하여 다음으로 가야할 목적지 x,y 좌표를 회귀 모델로 학습 시킨 후, 촬영한 이미지로부터 예측 좌표를 얻고 이를 arctan 함수를 통해 각도를 얻는 방식으로 활용하였습니다.
- 곡선 구간 적응형 주행
  - PID 제어를 활용해서 발생하는 오차를 줄이고자 하였고 동시에 즉각적으로 반응하고 안정적으로 주행 될 수 있도록 하였습니다. 

### 2. 🎨 색상 영역 인식
목적지 구분을 위한 색상 인식 시스템을 개발했습니다.

![색상 영역 인식](https://github.com/user-attachments/assets/b9625f0e-41cc-46e1-9cc8-89f54c1a614f)

**주요 기능:**
- 실시간 색상 영역 추적
- HSV 색공간 기반 정확한 색상 구분
  - 사용하는 색상들에 대한 최소,최대 HSV 값을 20개의 표본의 평균을 통해 측정하고 이를 색상 인식에 활용하였습니다.
- 다중 색상 동시 인식
  - 물건 위치, 최종 위치에 대한 색상 2개에 대한 영상처리 과정을 동시에 진행 하였습니다.

### 3. 🌐 IoT 시스템
센서 데이터 수집과 실시간 통신을 위한 IoT 인프라를 구축했습니다.

![IoT 시스템](https://github.com/user-attachments/assets/6b72599e-3c96-4b84-8267-0c5a051f1d86)

**주요 기능:**
- 실시간 센서 데이터 수집
  - AGV로부터 발생하는 작업 시작/종료/충돌 및 이미지 정보를 라즈베리파이로 전송하고 이를 클라우드 저장소에 저장하였습니다.  
- MQTT 기반 데이터 전송
  - 원격 GUI 컨트롤러로부터의 수동 조작 정보와 실시간 수하 위치 변동 정보를 MQTT통신을 통해 AGV에 전달 하였습니다.
- 클라우드 데이터 저장 및 분석
  - AGV별 작업정보를 클라우드 저장소에 저장하고, 이를 백엔드 프로그램(python)을 통해 파싱 및 분석하고 웹 대시보드에 반영하였습니다. 

### 4. 📱 웹 대시보드
직관적인 모니터링과 제어를 위한 웹 기반 대시보드를 개발했습니다.

![웹 대시보드](https://github.com/user-attachments/assets/b7603e72-7848-4bef-821c-e6b1ae820aa3)

**주요 기능:**
- 실시간 AGV 상태 모니터링
  - AGV 별 현재 작업의 작업시간/충돌/수동조작 정보와 이전 작업들의 정보를 시각화 하였습니다. 
- OpenAI 기반 AGV 분석
  - AGV 별 최근 10개의 작업정보를 기반으로 OpenAI를 활용해서 AGV 분석 정보 및 개선 사항을 표시하였습니다.
- 원격 제어 및 설정 변경
  - 섹션(Red, Green)별 물류 현황을 트래킹하여 사용률이 적은 섹션으로 AGV의 도착지를 실시간으로 변경 되도록 하였습니다. 

---

### 향후 개선사항
- 📌 딥러닝 모델 성능 향상
- 📌 다양한 환경 조건 대응
- 📌 다중 AGV 협업 시스템 구축

# 🚦 Rush Hour environment with Reinforcement Learning

> **Multi-Agent RL**을 이용해 Rush Hour 퍼즐을 최적화하는 프로젝트

---

## Project Overview
 - 고전 퍼즐 게임인 **Rush Hour**를 Custom 환경으로 구현  
 - **DQN 및 IQL 기반 Multi-Agent RL** 알고리즘을 적용하여 각 차량의 최적화된 움직임을 학습
- **문제 정의**: 교통 정체 상황에서 **각 차량의 움직임을 최소화**하여 **빠른 탈출 경로를 확보**
 

## Environment
- **환경**: 6x6 grid borad 위 차량 초기 배치
- **State**: 각 차량의 위치 및 차종(가로/세로), 목표 차량의 위치를 포함하는 그리드 상태
  ```Python
  vehicle_data = [
    {"x": 3, "y": 1, "length": 2, "orientation": "H", "movable": True}, # 목표 차량
    {"x": 4, "y": 2, "length": 2, "orientation": "H", "movable": True},
    # ... (다른 차량 데이터)]
  ```
- **Action**: (차량 인덱스, 이동 방향)으로 구성, 각 차량은 앞/뒤 두 가지 방향으로만 이동가능
- **Reward Design**:
  - 목표 차량이 이동 → +10
  - 불필요한 움직임 → -1
  - 차량 이동에 실패할 경우 → -10
  - 목표 도달 시 → +100
 
## Model
- **All-Random, DQN, IQL** 각각의 세 가지 알고리즘을 비교하여 **RushHour 퍼즐 해결 능력 비교**
- **DQN (Deep Q-Network)**: 개별 차량을 에이전트로 두고 Q-value 기반 학습 수행
- **IQL (Independent Q-Learning)**: 각 차량이 독립적으로 Q-function을 학습
- **하이퍼파라미터:**
  - **학습률(α)**: 0.6
  - **Discount factor(γ)**: 0.9
  - **탐험 전략**: ε-greedy (epsilon 초기값 0.2, epsilon_decay = 0.99, min_epsilon = 0.01)
  - **episode_num**: 5000
## Result
- All-Random
  <div align="left">
  난이도 중 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 난이도 상
  </div>
  <div align="left">
  <img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/d2e037a8-d7bc-4975-8b34-09f673ccf40b" />
  <img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/b4944fb8-8f27-462b-8de6-d3affe40d80f" />
  </div>
- DQN
  <div align="left">
  난이도 중 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 난이도 상
  <div align="left">
  <img src="https://github.com/user-attachments/assets/fb0748fa-d07f-407b-ae54-86983303863f" width="250"/>
  <img src="https://github.com/user-attachments/assets/baac4b98-ca13-4280-b64e-24058cc9147c" width="250"/>

  </div>
- IQL
  <div align="left">
  난이도 중
  </div>

  <img src="https://github.com/user-attachments/assets/529c6aca-2321-4281-b41c-77ca0bbebe70" width="250"/>
## 설치 및 실행
 **1. 프로젝트 클론**
```bash
  git clone https://github.com/rushHour-SMU/rushHour.git
  cd rushHour
  ```
 **2. 가상환경 설정**
```bash
python3 -m venv venv
```
 **3. 가상환경 활성화**
```bash
./activate_deactivate
```

 **4. 패키지 설치**
```bash
pip install -r requirements.txt
```

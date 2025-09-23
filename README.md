# 🚦 Rush Hour environment with Reinforcement Learning

> **Multi-Agent RL**을 이용해 Rush Hour 퍼즐을 최적화 하는 프로젝트

---

## Project Overview
Rush Hour 퍼즐 custom 환경을 제작  
**DQN & Independent Q-learning 기반 Multi-Agent RL 알고리즘**을 적용한 차량의 개별 움직임 최적화 

**문제 정의**: 교통 정체 상황에서 각 차량의 움직임을 최소화 하면서 문제를 해결할 수 있는가?
**목표**: 각 차량을 독립적으로 학습하여 **빠른 탈출 경로 확보** 및 **정체 최소화**  
**기술 스택**: Python, PyTorch, OpenAI Gym  
**환경**: 자체 제작 Rush Hour 환경  

## Environment
**환경**: 6x6 보드 위에서 다양한 차량이 유기적으로 배치된 환경 구성
**State**: 각 차량의 위치 및 차종(가로/세로), 목표 차량의 위치
**Reward Design**:
- 목표 차량이 이동 → +10
- 불필요한 움직임 → -1
- 목표 도달 시 → +100
 
## Model & Methodology
**DQN (Deep Q-Network)**: 개별 차량을 에이전트로 두고 Q-value 기반 학습 수행
**Independent Q-Learning (IQL)**: 각 차량이 독립적으로 Q-function을 학습
**하이퍼파라미터:**
- 학습률: 1e-3
- 감가율(γ): 0.99
- 탐험 전략: ε-greedy (ε=1.0 → 0.1, linear decay)

## 설치 및 실행
 1. 프로젝트 클론
```bash
  git clone https://github.com/rushHour-SMU/rushHour.git
  cd rushHour
  ```
 2. 가상환경 설정
  가상환경 만들기
  프로젝트 디렉토리에서 가상환경을 생성합니다:

```bash
python3 -m venv venv
```
- 가상환경 활성화
```bash
./activate_deactivate
```

3. 패키지 설치

- `requirements.txt` 파일에 정의된 의존성 패키지들을 설치하려면 아래 명령어를 실행합니다:
```bash
pip install -r requirements.txt
```

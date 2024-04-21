# CPU 스케줄링

## CPU 스케줄링의 정의

CPU 스케줄링은 운영 체제가 프로세스들 사이에서 CPU 자원을 어떻게 할당할지 결정하는 프로세스 관리 기법이다.

## CPU 스케줄러
- 여러 프로세스의 상황을 고려하여 CPU와 시스템 자원의 배정을 결정

## 고수준 스케줄링
- 시스템 내의 전체 작업 수를 조절한다.
- 어떤 작업을 시스템이 받아들일지 또는 거부할지 결정한다.
- 시스템 내에서 동시에 실행 가능한 프로세스의 총 개수가 정해진다.
- 장기 스케줄링, 작업 스케줄링, 승인 스케줄링이라고도 함.
- **장기(long_term or job) 스케쥴러(scheduler)**
  - 프로세스를 디스크에서 메모리로 적재한다. 
    - loads the process image from the disk to memory
  - 적재기(“loader”)와 메모리관리 모듈과 연관성이 있다.
  - 멀티프로그래밍의 정도를 제어한다. 
    - controls the degree of multiprogramming
  - I/O_bound process vs. CPU_bound process

## 중간 수준 스케줄링
- 중지와 활성화로 전체 시스템의 활성화된 프로세스 수를 조절하여 과부하를 막는다.
- 일부 프로세스를 중지 상태로 옮김으로써 나머지 프로세스가 원만하게 작동하도록 지원한다.
- 저수준 스케줄링이 원만하게 이루어지도록 완충하는 역할을 한다.
- **중기(medium_term) 스케줄러(scheduler)** 또는 swapper라고도 함
  - 멀티프로그램의 정도를 줄인다. 
    - to reduce the multiprogramming degree
  - 프로세스 이미지를 메인메모리에서 디스크로 내보낸다. 
    - swap out the process image from main memory to hard disk

## 저수준 스케줄링
- 어떤 프로세스에 CPU를 할당할지, 어떤 프로세스를 대기 상태로 보낼지 등을 결정한다.
- 아주 짧은 시간에 일어나기 때문에 단기 스케줄링이라고도 함.
- **단기(short_term or CPU) 스케쥴러(scheduler)**
  - 준비 상태의 프로세스 중 하나를 선택하여 CPU를 할당한다. 
    - select the process that are ready to execute or “from the ready queue”
    - allocate the CPU to one of them → “dispatcher”

## 스케줄링의 연관성
- **고수준 스케줄링**은 전체 시스템의 부하를 고려하여 작업을 시작할지 말지를 결정한다.
- **중간 수준 스케줄링**은 시스템에 과부하가 걸려서 전체 프로세스 수를 조절해야 한다면 이미 활성화된 프로세스 중 일부를 보류 상태로 보낸다.
- **저수준 스케줄링**은 실제 작업을 수행한다.

## CPU 스케줄링의 목적

- **공평성**:
  모든 프로세스가 자원을 공평하게 배정받아야 하며, 자원 배정 과정에서 특정 프로세스가 배제되어서는 안 된다.

- **효율성**:
  시스템 자원이 유휴 시간 없이 사용되도록 스케줄링을 하고, 유휴 자원을 사용하려는 프로세스에는 우선권을 주어야 한다.

- **안정성**:
  우선순위를 사용하여 중요 프로세스가 먼저 작동하도록 배정함으로써 시스템 자원을 점유하거나 파괴하려는 프로세스로부터 자원을 보호해야 한다.

- **확장성**:
  프로세스가 증가해도 시스템이 안정적으로 작동하도록 조치해야 하며 시스템 자원이 늘어나는 경우 이 혜택이 시스템에 반영되게 해야 한다.

- **반응 시간 보장**:
  응답이 없는 경우 사용자는 시스템이 멈춘 것으로 가정하기 때문에 시스템은 적절한 시간 안에 프로세스의 요구에 반응해야 한다.

- **무한 연기 방지**:
  특정 프로세스의 작업이 무한히 연기되어서는 안 된다.


## 선점형 스케줄링

- **정의**: 운영체제가 필요하다고 판단하면 실행 상태에 있는 프로세스의 작업을 중단시키고 새로운 작업을 시작할 수 있는 방식이다.
- **적합성**: 하나의 프로세스가 CPU를 독점할 수 없기 때문에 빠른 응답 시간을 요구하는 대화형 시스템이나 시분할 시스템에 적합하다.
- **사용**: 대부분의 저수준 스케줄러는 선점형 스케줄링 방식을 사용한다.

## 비선점형 스케줄링

- **정의**: 어떤 프로세스가 실행 상태에 들어가 CPU를 사용하면 그 프로세스가 종료되거나 자발적으로 대기 상태에 들어가기 전까지는 계속 실행되는 방식이다.
- **장점**: 선점형 스케줄링보다 스케줄러의 작업량이 적고 문맥 교환에 의한 낭비도 적다.
- **단점**: CPU 사용 시간이 긴 프로세스 때문에 CPU 사용 시간이 짧은 여러 프로세스가 오랫동안 기다리게 되어 전체 시스템의 처리율이 떨어진다.
- **역사**: 과거의 일괄 작업 시스템에서 사용하던 방식이다.


## 프로세스 우선순위

- **커널 프로세스**: 커널 프로세스의 우선순위가 일반 프로세스보다 높다.
- **우선순위의 영향**: 시스템에는 다양한 우선순위의 프로세스가 공존하며, 우선순위가 높은 프로세스가 CPU를 먼저, 더 오래 차지한다.
- **우선순위 표현**: 시스템에 따라 높은 숫자가 높은 우선순위를 나타내기도 하고, 낮은 숫자가 높은 우선순위를 나타내기도 한다.

## CPU집중 프로세스와 입출력 집중 프로세스

- **CPU 집중 프로세스 (CPU-bound process)**
  - 수학 연산과 같이 CPU를 많이 사용하는 프로세스로, CPU 버스트가 많은 특징을 가짐.

- **입출력 집중 프로세스 (I/O-bound process)**
  - 저장장치에서 데이터를 복사하는 일과 같이 입출력을 많이 사용하는 프로세스로, 입출력 버스트가 많은 특징을 가짐.

## 준비 상태의 다중 큐

- 프로세스는 준비 상태에 들어올 때마다 자신의 우선순위에 해당하는 큐의 마지막에 삽입된다.
- CPU 스케줄러는 우선순위가 가장 높은 큐(0번 큐)의 맨 앞에 있는 프로세스에게 CPU를 할당한다.


## 프로세스의 우선순위를 배정하는 방식

### 고정 우선순위 방식
- 운영체제가 프로세스에 우선순위를 부여하면 프로세스가 끝날 때까지 바뀌지 않는다.
- 프로세스가 작업하는 동안 우선순위가 변하지 않아 구현하기 쉽다.
- 시스템의 상황이 변하는데 우선순위를 고정하면 시스템의 변화에 대응하기 어려워 작업 효율이 떨어진다.

### 변동 우선순위 방식
- 프로세스 생성 시 부여받은 우선순위가 프로세스 작업 중간에 변할 수 있다.
- 구현하기 어렵지만 시스템의 효율성을 높일 수 있다.

## 대기 상태의 다중 큐

### 개념
- 시스템의 효율을 높이기 위해 대기 상태에서는 같은 입출력을 요구하는 프로세스끼리 모아놓는다.

### 다중 큐 비교

#### 준비 큐
- 한 번에 하나의 프로세스를 꺼내어 CPU를 할당한다.

#### 대기 큐
- 여러 개의 프로세스 제어 블록을 동시에 꺼내어 준비 상태로 옮긴다.
- 대기 큐에서 동시에 끝나는 인터럽트를 처리하기 위해 인터럽트 벡터라는 자료 구조를 사용한다.

### 스케줄링 알고리즘의 종류
- **비선점형 알고리즘**: FCFS 스케줄링, SJF 스케줄링, HRN 스케줄링
- **선점형 알고리즘**: 라운드 로빈 스케줄링, 다단계 큐 스케줄링, 다단계 피드백 큐 스케줄링
- **둘 다 가능**: 우선순위 스케줄링

### 스케줄링 알고리즘의 평가 기준

#### CPU 사용률
- 전체 시스템의 동작 시간 중 CPU가 사용된 시간을 측정하는 방법
- 가장 이상적인 수치는 100%이지만 실제로는 여러 가지 이유로 90%에도 못 미침

#### 처리량
- 단위 시간당 작업을 마친 프로세스의 수
- 이 수치가 클수록 좋은 알고리즘임
- 
- **대기 시간**: 프로세스가 생성된 후 실행되기 전까지 대기하는 시간

- **응답 시간**:첫 작업을 시작한 후 첫 번째 출력(반응)이 나오기까지의 시간

- **실행 시간**: 프로세스 작업이 시작된 후 종료되기까지의 시간

- **반환 시간**: 대기 시간을 포함하여 실행이 종료될 때까지의 시간

#### 평균 대기 시간
- 모든 프로세스의 대기 시간을 합한 뒤 프로세스의 수로 나눈 값
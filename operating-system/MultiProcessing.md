# 다중 처리시스템(Multi Processing)

## 다중프로세서 (Multiprocessor)
- 시스템 내에서 다수의 프로세서 사용
- I/O 프로세서(=채널), 디스크 컨트롤러 등 포함

**비교:**
- 다중프로세서(Multiprocessor): 여러 프로세서가 하나의 컴퓨팅 작업을 수행하기 위해 협력하는 시스템
- 병렬프로세서(Parallel Processor): 여러 계산 작업을 동시에 처리하는 시스템
- 멀티코어/매니코어(Multi-core or Many-core): 단일 컴퓨팅 구성 요소에 여러 개의 독립적인 실제 중앙 처리 장치(코어)가 있는 시스템

**다중처리:**
- 소프트웨어적 개념
- 시분할 시스템(Time sharing systems)으로 발전

## 멀티 프로그래밍의 문제점과 멀티 프로세싱의 해결책

- **멀티 프로그래밍의 문제점:**
    - 프로그램이 I/O 작업을 요청할 때 CPU가 유휴 상태(idle)가 되는 경우가 발생.
      - 이는 CPU 자원이 낭비되는 주요 원인.

- **멀티 프로세싱의 해결책:**
    - 멀티 프로세싱은 여러 CPU를 사용하여 한 프로세스가 I/O를 대기하는 동안 다른 프로세스가 CPU에서 실행되어 CPU 유휴 시간을 최소화.
      - 이로 인해 시스템 자원의 유휴 시간 감소와 자원 활용도가 향상되며, 전체적인 시스템 성능이 개선.

# 운영체제 개요

## 운영체제 정의 및 기능

### 운영체제 정의
- 컴퓨터 사용자와 하드웨어 사이에서 중재자 역할 수행
- 사용자/컴퓨터 인터페이스로서, 사용자가 컴퓨터 사용 용이하게 지원, 컴퓨팅 환경 제공

### 사용자 관점에서의 운영체제 기능
- 프로그램 개발, 실행 지원
- 입출력 장치, 파일, 시스템 접근 용이하게 관리
- 에러 발견 및 처리, 어카운팅 기능 제공

### 시스템 관점에서의 운영체제 기능
- 시스템 자원 효율적 관리
- 자원 관리자 역할로, 시스템 자원 및 프로세스 효율적으로 운용

## 운영체제의 역할

- 사용자와의 인터페이스 정의
- 사용자들이 하드웨어 공동 사용하도록 관리
- 사용자들 간 데이터 공유 허용
- 자원 스케줄링 및 할당자로서의 기능 수행
- 입출력 보조 역할 수행
- 오류 처리 기능 제공

## 운영체제의 목적

- **시스템 성능 및 생산성 향상**:
    - **처리능력(Throughput)**: 시간당 처리할 수 있는 작업량을 최대화
    - **신뢰도(Reliability)**: 주어진 기능을 실패 없이 수행할 수 있는 능력 강화
    - **응답시간(Response Time)**: 사용자 요청 후 시스템 반응까지의 시간 단축
    - **사용가능도(Availability)**: 고장이나 오류 발생 시에도 시스템 운영에 미치는 영향 최소화

## 운영체제의 구

운영체제는 다양한 중요 구성 요소로 이루어짐. 각 구성 요소는 시스템의 원활한 작동을 보장하는 데 필수적인 역할을 수행.

### 1. 프로세스 관리
- **프로세스 스케줄링**: 다양한 프로세스가 CPU 시간을 공정하게 사용하도록 관리
- **프로세스 생성 및 제거**: 프로세스의 생명 주기를 관리하며, 필요에 따라 생성하고 종료

### 2. 메모리 관리
- **메모리 할당**: 각 프로세스에 필요한 메모리 공간을 할당
- **페이징 및 세그먼테이션**: 메모리를 효율적으로 사용하고 프로세스 간 격리를 유지하기 위한 기술적 방법

### 3. 파일 시스템 관리
- **파일 생성 및 삭제**: 사용자 및 시스템의 요구에 따라 파일을 생성하고 삭제
- **디렉터리 관리**: 파일과 프로그램을 조직화하고 접근을 용이하게 함

### 4. 장치 관리
- **입출력 제어**: 하드웨어 장치와의 입출력을 관리
- **드라이버 인터페이스**: 다양한 하드웨어에 대한 접근을 중재

### 5. 보안 및 보호 기능
- **접근 제어**: 사용자나 프로세스의 자원 접근 권한을 관리
- **암호화 및 감사**: 데이터 보호와 시스템 사용에 대한 감사 수행

이러한 구성 요소들은 통합되어 복잡한 시스템인 컴퓨터의 효율적이고 안전한 운영을 지원.

## 운영체제의 발전 과정

운영체제의 발전은 컴퓨터 기술의 발전과 밀접하게 연결되어 있으며, 사용자의 요구와 기술의 발전에 따라 여러 단계를 거쳐 진화함.

### 1. 순차처리 시스템
- **정의**: 하나의 작업이 완료된 후 다음 작업이 시작하는 가장 기본적인 처리 방식.
- **특징**: 작업 간 전환에 시간이 많이 소요되며, 자원 활용도가 매우 낮음.

### 2. 단순일괄 처리시스템 (Simple Batch Processing System)
- **정의**: 여러 작업을 일정량 모아 순차적으로 처리하는 시스템.
- **특징**: 자동화된 작업 처리를 가능하게 하지만, 작업의 우선순위나 긴급성을 반영하기 어려움.

### 3. 멀티프로그래밍 일괄처리시스템 (Multiprogramming Batch System)
- **정의**: 여러 프로그램을 메모리에 동시에 적재하여 CPU의 유휴 시간을 최소화하는 시스템.
- **특징**: 시스템 자원의 활용도를 극대화하지만, 복잡한 자원 관리와 스케줄링 알고리즘이 필요.

### 4. 시분할 시스템 (Time-Sharing System)
- **정의**: 멀티태스킹을 통해 여러 사용자가 동시에 시스템을 사용할 수 있도록 하는 시스템.
- **특징**: 각 사용자에게 CPU 시간을 일정량 할당하여 신속한 응답 시간을 제공. 사용자 입장에서는 마치 전체 시스템을 독점하고 있는 것처럼 느껴짐.

## 초기의 운영체제
### 1940년대
- 직접 기계어 사용
- 모든 명령어 코딩 필요
- Front panel switch 사용
- 콘솔에서 프로그램 수행 감시
- Paper tape과 punch card 사용
- 하드디스크 없음 (Not exist the hard disk)

### 운영체제 없는 경우 프로그램 수행 절차
1. bootstrap loader -> memory
2. compiler -> memory
3. source program -> card reader -> memory
4. execute compiler
5. run program

### 용어 정리
- 작업(Task) = 잡(Job) = 프로그램(program) -> 프로세스(Process)로 변환

### 문제점
- 작업 준비 시간 (Job setup time)
- 작업 철거 시간 (Job teardown time)
- 작업 변환 시간 (Job transition time)

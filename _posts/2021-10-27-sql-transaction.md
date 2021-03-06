---
title: "데이터베이스 트랜잭션이란?"
date: 2021-10-27
categories: SQL
---

### Transaction이란 무엇인가?

---

데이터베이스는 항상 정확하고 일관된 상태를 유지할 수 있도록 다양한 기능을 제공하는데 그 중 한가지인 **트랜잭션**은
데이터베이스의 상태를 변환시키는 논리적인 작업의 단위이며 한번에 모두 수행되어야 하는 일련의 연산을 뜻한다.
또한 장애가 발생했을 때 데이터를 복구하는(Rollback) 작업의 단위이기도 하다.

트랜잭션은 거래라는 의미를 가지며 은행이나 데이터베이스의 시스템에서 사용되는 기능이다.
송금 거래로 예를 들면 송금시에 K은행의 계좌에서 돈이 빠져나가고 S은행에 계좌에 입금이 되어야 
비로소 거래가 성공적으로 끝난다고 할 수 있는데 이러한 거래가 하나의 트랜잭션을 구성한다.

트랜잭션은 한번에 모두 수행되어야 하는 연산이며 K은행의 계좌에서 돈은 빠져나갔지만 S은행의 계좌에는 
입금이 안되는 상황이 생기면 안되므로 거래가 성공적으로 끝났을 경우에만 거래를 승인하고(commit) 
돈이 빠져나가지 않거나 입금이 안되는 상황이 발생했을 경우에는 거래를 취소(Rollback)하여 송금 전의 상황으로 되돌리는 것이다.

이렇게 데이터베이스가 정확하고 일관된 상태를 유지할 수 있도록 하는 기능이 트랜잭션인데
데이터베이스의 작업 도중에 데이터를 삽입, 수정하거나 삭제를 하는 일련의 과정에서
오류가 발생한다면 작업을 원상태로 되돌리게 되고 처리 과정들이 모두 성공적인 경우에만 최종적으로 데이터베이스에 반영하게 된다.

---

### 트랜잭션의 특징

- 트랜잭션은 데이터베이스 시스템에서 병행 제어 및 회복 작업 시 처리되는 작업의 논리적 단위이다.
- 사용자가 시스템에 대한 서비스 요구 시 시스템이 응답하기 위한 상태 변환 과정의 작업 단위이다.
- 하나의 트랜잭션은 commit 되거나 rollback 된다.

---

### 트랜잭션의 성질

- **원자성 (Atomicity)**
  - 트랜잭션의 연산은 데이터베이스에 모두 반영되든지 아니면 전혀 반영되지 않아야 한다.
  - 트랜잭션 내의 모든 명령은 반드시 완벽히 수행되어야 하며, 모두가 완벽히 수행되지 않고 어느하나라도 오류가 발생하면 트랜잭션 전부가 취소되어야 한다.
- **일관성 (Consistency)**
  - 트랜잭션이 그 실행을 성공적으로 완료하면 언제나 일관성 있는 데이터베이스 상태로 변환한다.
  - 시스템이 가지고 있는 고정요소는 트랜잭션 수행 전과 트랜잭션 수행 완료 후의 상태가 같아야 한다.
- **독립성 (Isolation)**
  - 둘 이상의 트랜잭션이 동시에 병행 실행되는 경우 어느 하나의 트랜잭션 실행중에 다른 트랜잭션의 연산이 끼어들 수 없다.
  - 수행중인 트랜잭션은 완전히 완료될 때까지 다른 트랜잭션에서 수행 결과를 참조할 수 없다.
- **지속성 (Durability)**
  - 성공적으로 완료된 트랜잭션의 결과는 시스템이 고장나더라도 영구적으로 반영되어야 한다.

---

### 트랜잭션의 연산

- **Commit**

commit은 한 개의 트랜잭션에 대한 작업이 성공적으로 끝났고 데이터베이스가 다시 일관된 상태에 있을 때 이 트랜잭션이 행한 갱신 연산이 완료된 것을 트랜잭션 관리자에게 알려주는 연산이다.

- **Rollback**

하나의 트랜잭션 처리가 비정상적으로 종료되어 데이터베이스의 일관성을 깨뜨렸을 때 이 트랜잭션의 일부가 정상적으로 처리되었더라도 트랜잭션의 원자성을 구현하기 위해 이 트랜잭션이 행한 모든 연산을 취소하는 연산으로 rollback시에는 해당 트랜잭션을 재시작하거나 폐기한다.

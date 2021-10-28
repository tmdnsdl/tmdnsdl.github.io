---
title: "데이터베이스 트랜잭션이란?"
date: 2021-10-27
categories: SQL
---

### Transaction이란 무엇인가?

---

데이터베이스는 항상 정확하고 일관된 상태를 유지할 수 있도록 다양한 기능을 제공하는데 그 중 한가지인 트랜잭션은
데이터베이스의 논리적인 작업의 단위이며 장애가 발생했을 때 데이터를 복구하는(Rollback) 작업의 단위이다.

트랜잭션은 거래라는 의미를 갖고 송금 거래로 트랜잭션을 설명할 수 있다.
K은행에서 S은행으로 송금 거래로 예를 들면
K은행의 계좌에서 돈이 빠져나가고 S은행에 계좌에 입금이 되어야 비로소 거래가 성공적으로 끝난다고 할 수 있는데
이 과정에서 K은행의 계좌에서 돈은 빠져나갔지만 S은행의 계좌에는 입금이 안되는 상황이 생기면 안되기에
거래가 성공적으로 끝났을 경우에만 거래를 승인하고(commit) 그렇지 않고 돈이 빠져나가지 않거나 입금이 안되는
상황이 발생했을 경우에는 거래를 취소(Rollback)하여 송금 전의 상황으로 되돌리는 것이다.

이렇게 데이터베이스의 정확하고 일관된 상태를 유지할 수 있도록 하는 기능의 트랜잭션인데
데이터베이스의 작업 도중에 데이터를 삽입, 수정하거나 삭제를 하는 일련의 과정에서
오류가 발생한다면 작업을 원상태로 되돌리는 기능을 한다.
최종적으로 처리 과정들이 모두 성공적인 경우에만 최종적으로 데이터베이스에 반영하게 된다.

송금 거래에서 출금과 입금 두가지 모두가 성공적이어야 하는 것과 같이
데이터베이스의 일련의 작업도 하나만 성공적이면 안되므로 작업의 단위를 갖는 것이라고 할 수 있다.



트랜잭션의 특징은 4가지로 구분된다
- 원자성 (Atomicity)
- 일관성 (Consistency)
- 독립성 (Isolation)
- 지속성 (Durability)



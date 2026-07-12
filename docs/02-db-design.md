# Database Design

## Development Tool

* MySQL

---

# Database Concepts

## Primary Key (PK)

Primary Key(PK)는 **각 데이터를 구분하기 위한 고유한 번호**이다.

예를 들어 사용자 정보는 다음과 같이 구분할 수 있다.

| user_id (PK) | nickname |
| ------------ | -------- |
| 1            | sungwook |
| 2            | tanaka   |
| 3            | yuki     |

`user_id`는 사용자를 식별하는 고유 번호이며, 같은 값이 중복될 수 없다.

---

## Foreign Key (FK)

Foreign Key(FK)는 **다른 테이블의 Primary Key(PK)를 참조하여 두 테이블을 연결하는 컬럼**이다.

예를 들어 메시지 테이블은 사용자를 직접 저장하는 것이 아니라 `user_id`를 저장하여 사용자를 구분한다.

| message_id | user_id (FK) | message  |
| ---------- | ------------ | -------- |
| 1          | 1            | 안녕하세요    |
| 2          | 2            | こんにちは    |
| 3          | 1            | 잘 부탁드립니다 |

`messages.user_id`는 `users.user_id`를 참조한다.

---

## Reference

참조(Reference)란 **외래키(FK)를 이용하여 다른 테이블의 데이터를 조회하는 것**을 의미한다.

예를 들어 `messages.user_id = 1`이라면 `users.user_id = 1`을 찾아 해당 메시지의 작성자가 누구인지 확인할 수 있다.

---

# Entity Design

현재 프로젝트는 **익명 채팅**과 **채팅 기록 저장**을 목표로 한다.

회원가입 기능은 없지만 사용자를 구분해야 하므로 다음 두 개의 엔티티를 사용한다.

* User
* Message

---

# User Entity

## 역할

채팅 참여자를 관리한다.

### 컬럼

| 컬럼명      | 설명          |
| -------- | ----------- |
| user_id  | 사용자 번호 (PK) |
| nickname | 닉네임         |

### 사용 목적

* 사용자 구분
* 닉네임 표시
* 닉네임 중복 검사
* 메시지 작성자 식별

---

# Message Entity

## 역할

채팅 메시지를 저장한다.

### 컬럼

| 컬럼명             | 설명          |
| --------------- | ----------- |
| message_id      | 메시지 번호 (PK) |
| user_id         | 사용자 번호 (FK) |
| original_text   | 원본 메시지      |
| translated_text | 번역 메시지      |
| created_at      | 전송 시간       |

### 사용 목적

* 채팅 기록 저장
* 번역 결과 저장
* 전송 시간 저장
* 이전 채팅 기록 조회

---

# Entity Relationship

User와 Message는 **1:N 관계**이다.

* 한 명의 사용자는 여러 개의 메시지를 작성할 수 있다.
* 하나의 메시지는 한 명의 사용자에게만 속한다.

```text
User (1)
 ├── user_id (PK)
 └── nickname
        │
        │ 1 : N
        ▼
Message (N)
 ├── message_id (PK)
 ├── user_id (FK)
 ├── original_text
 ├── translated_text
 └── created_at
```

---

# Why Separate the Tables?

User와 Message를 분리한 이유는 다음과 같다.

* 사용자 정보와 채팅 기록을 분리하여 관리하기 위해
* 같은 닉네임을 반복 저장하지 않아 데이터 중복을 줄이기 위해
* `user_id`를 통해 메시지 작성자를 쉽게 조회하기 위해
* 데이터 구조를 확장하기 쉽게 만들기 위해

---

# Final Database Structure

## User

```text
user_id (PK)
nickname
```

## Message

```text
message_id (PK)
user_id (FK)
original_text
translated_text
created_at
```

---

# Summary

* **PK (Primary Key)** : 데이터를 구분하는 고유 번호
* **FK (Foreign Key)** : 다른 테이블의 PK를 참조하는 연결 번호
* **Reference** : FK를 이용해 다른 테이블의 데이터를 조회하는 것
* **User** : 채팅 참여자를 관리하는 엔티티
* **Message** : 채팅 메시지를 관리하는 엔티티
* **Relationship** : User 1 : N Message

# Translator Chat

Korean-Japanese Translation Chat Service

## 프로젝트 소개
실시간 번역 채팅 서비스

## 기능 요구사항

1. 사용자는 닉네임을 입력하여 채팅방에 입장할 수 있다.
2. 사용자는 닉네임 중복 검사를 수행할 수 있다.
3. 2명 이상의 사용자가 실시간 채팅할 수 있다.
4. 사용자 닉네임을 표시한다.
5. 사용자 메시지를 채팅창 왼쪽에 출력한다.
6. 번역봇 메시지를 채팅창 오른쪽에 출력한다.
7. 사용자가 입력한 모든 메시지를 자동 번역한다.
8. 번역 결과를 채팅창에 출력한다.
9. 현재 접속 중인 사용자 목록을 표시한다.
10. 채팅 기록을 DB에 저장한다.
11. 사용자가 재접속 시 이전 채팅 기록을 조회할 수 있다.
12. 한국어 ↔ 일본어 번역을 지원한다.

## 비기능 요구사항

1. Discord 스타일 UI 구현
2. 실시간 메시지 전송
3. 반응형 웹 지원
4. 사용자 식별 가능

## Tech Stack

### Frontend

- React
- HTML
- CSS
- JavaScript

### Backend

- Java 21
- Kotlin
- Spring Boot
- JPA (Hibernate)

### Database

- MySQL

### IDE

- VS Code
- IntelliJ IDEA Community Edition

### Version Control

- Git
- GitHub

### API Testing

- Postman (미정)

### Testing

- Spring Boot Test

### Server & Deployment

#### Development

- Local Server

#### Deployment

- AWS (Planned)

## 개발 로드맵

### 완료

- [x] 요구사항 정리
- [x] 화면 설계 (와이어프레임)
- [x] 기술 스택 결정

### 진행 예정

- [ ] DB 설계 (ERD)
- [ ] API 설계
- [ ] UI 구현
- [ ] 실시간 채팅 구현
- [ ] DB 연결
- [ ] 번역 API 연결
- [ ] 사용자 식별 기능 구현
- [ ] 테스트 및 개선

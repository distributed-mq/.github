# MQ-Based Distributed System 🚀

## 🔹 Overview
- 이 프로젝트는 메시지 큐(Message Queue) 기반의 비동기 처리 시스템을 구축하는 예제입니다.
- 프론트엔드(FE), 프로듀서(Producer), 컨슈머(Consumer), 로드밸런서(NGINX) 등을 연동하여 시스템을 구성합니다.
- 핵심적으로 **RabbitMQ**가 메시지 큐 역할을 수행하며, 작업을 분산 처리하고 확장성을 극대화하는 것을 목표로 합니다.

## 📌 프로젝트 구조
이 프로젝트는 다음과 같은 독립적인 서비스로 구성됩니다:

- **Frontend**: React 기반 UI
- **Backend Producer**: Spring Boot API 서버 (RabbitMQ에 메시지 전송)
- **Backend Consumer**: Worker 서버 (RabbitMQ에서 메시지를 소비)
- **Message Queue**: RabbitMQ 설정 및 운영
- **NGINX**: Reverse Proxy & Load Balancer

## ⚙️ 시스템 아키텍처

📌 **전체 시스템 흐름**

1️⃣ **[FE] React**
   - "작업 추가" 요청 → 백엔드(Producer) API 호출

2️⃣ **[BE - Producer] Spring Boot API 서버**
   - 요청을 받아 MQ(RabbitMQ)에 메시지 전송

3️⃣ **[MQ] RabbitMQ**
   - 메시지를 대기열(Queue)에 저장

4️⃣ **[NGINX] 로드밸런서**
   - Worker(Consumer) 서버로 메시지를 분배

5️⃣ **[BE - Consumer] Spring Boot Worker 서버**
   - RabbitMQ에서 메시지를 꺼내 실제 작업 수행

---
# the default layout is 'page'
icon: fas fa-info-circle
order: 4
---

# 김환 / Hwan Kim

AI Engineer이자 Full-stack / Systems 개발자로 일하고 있습니다. 게임 환경에서 LLM 기반 NPC, 스토리 Agent, World State, Memory, Rule Engine이 어떻게 함께 동작할 수 있는지에 관심이 많습니다.

연구 아이디어를 실제 동작하는 시스템으로 만들고, 지연 시간, 일관성, 운영 안정성 같은 현실적인 제약까지 함께 다루는 일을 좋아합니다. 이 블로그에는 AI Agent, 게임 시스템, 백엔드 운영, 연구 구현 과정에서 배운 내용을 정리합니다.

## 현재 관심사

- 게임 환경을 위한 LLM Agent 시스템
- NPC Memory, World State, Event Trigger, Rule Engine
- RAG, Knowledge Graph, FAISS 기반 장기 기억 구조
- FastAPI, Redis, PostgreSQL, WebSocket 기반 AI 서비스 운영
- C# 클라이언트, TCP 통신, UI 이벤트, 상태 관리
- GNN, Computer Vision, 이상 영역 탐지 연구

## 주요 프로젝트

### Animus

로컬 LLM 기반 저지연 NPC 대화 엔진을 개인 R&D로 개발하고 있습니다. Anima와 Persona로 역할을 나누어 LLM 생성 경로와 플레이어 응답 경로를 분리하고, NPC_ID, Topic, WorldHash 기반 Response Cache를 통해 플레이어가 체감하는 응답 지연을 줄이는 구조를 실험했습니다.

핵심 관심사는 단순히 NPC의 문장을 생성하는 것이 아니라, 게임 내 세계 상태 변화와 NPC 기억, 관계, 사건 흐름이 장기적으로 일관되게 유지되는 구조를 만드는 것입니다.

### WorldWeaver

세계관 그래프 기반 인터랙티브 스토리 게임 시스템입니다. 세계관 문서를 Knowledge Graph로 변환하고, NPC별 Memory Graph, FAISS RAG, RuleEngine을 결합해 스토리 진행, 선택지, NPC 대화, 퀘스트, 전투, 인벤토리, 세이브/로드 같은 게임 상태를 관리하는 구조를 구현했습니다.

LLM은 말투와 서사를 담당하고, 사실 관계와 규칙 검증은 그래프와 RuleEngine이 담당하도록 책임을 분리했습니다.

### TCP_Talk

C# 기반 TCP 채팅 / 네트워크 프로토콜 구현 프로젝트입니다. TCP Socket 기반 메시지 송수신, 메시지 타입별 처리, 데이터 파싱, 연결 종료와 예외 상황 처리를 구현했습니다.

GUI 클라이언트에서는 사용자 입력, 버튼/키 이벤트, delegate/event 기반 상태 전달, 수신 스레드의 UI 갱신 흐름을 다뤘습니다. 이 경험을 통해 클라이언트 개발에서 입력 처리, 상태 변화, 화면 반영, 예외 처리가 하나의 흐름으로 이어져야 한다는 점을 배웠습니다.

## 경험

### 한국진로적성센터 / OCTAGNOSIS

2025년 12월부터 풀스택 프리랜서로 운영 서비스 개선과 AI 서비스 구축을 맡고 있습니다.

- FastAPI, Gemini API, Redis, PostgreSQL 기반 AI 분석 서버 구축
- Node.js / Express, Playwright, Piscina Worker Pool 기반 PDF 생성 서버 운영
- Next.js 15 관리자 시스템 기능 개선 및 리팩토링
- GitHub Actions, GHCR, Docker 기반 CI/CD 구축
- Windows Server / IIS 기반 서비스를 AWS Lightsail Ubuntu + Nginx Gateway 구조로 이전
- SQL Injection 위험 코드 수정, 검사 결과 무단 접근 취약점 차단
- 20,636건 데이터 전수 조사로 무결성 누락 39건 발견
- PostgreSQL 성능 진단, 중복 인덱스와 임시파일 문제 분석

기존 운영 서비스를 분석하고, 장애 가능성을 줄이며, 수동 패치에 의존하던 부분을 자동화 가능한 구조로 바꾸는 일을 해왔습니다.

## 연구

명지대학교 대학원 정보통신공학과에서 석사 학위를 받았습니다. 석사 논문은 GNN의 노이즈 적응 보정 구조를 다룬 **Modular GNN NAC: Noise-Adaptive Correction of Graph Neural Networks Using Attention Discrepancy**입니다.

연구 경험은 GNN, Computer Vision, 객체 탐지, 이상 영역 탐지에 걸쳐 있습니다. GAT 기반 노이즈 억제, UAV 영상 경량화 객체 탐지, U-ISORD 이상 영역 탐지 관련 논문을 게재했고, GNN 기반 멀티센서 데이터 노이즈/중복 탐지와 Unknown Object 탐지 관련 특허 출원 경험이 있습니다.

최근에는 **Anima/Persona: Dual-Agent NPC Dialogue** 주제로 IEEE CoG 2026 short paper를 제출했습니다.

## 기술 스택

- **LLM / Agent**: Gemma, Gemini, LangChain LCEL, Pydantic v2, RAG, FAISS, Knowledge Graph
- **Backend / Serving**: FastAPI, WebSocket, Express, Redis, PostgreSQL, Prometheus, Grafana
- **Frontend / Client**: React, Next.js, TypeScript, Vite, C#, Unity
- **Systems / Infra**: Docker, GitHub Actions, GHCR, Nginx, AWS Lightsail, Ubuntu, Windows Server / IIS
- **Research / Data**: PyTorch Geometric, GNN, NetworkX, Computer Vision, EXPLAIN ANALYZE

## 학력

- 명지대학교 대학원 정보통신공학과 석사, 2025.08
- 한국성서대학교 컴퓨터소프트웨어학과 학사, 2023.08

## 링크

- GitHub: [kimhwan1103](https://github.com/kimhwan1103)
- Demo / Portfolio: [worldweaver-demo-production.up.railway.app](https://worldweaver-demo-production.up.railway.app)
- Email: [rlaghks1103@gmail.com](mailto:rlaghks1103@gmail.com)

---

# English

## Hwan Kim

I am an AI Engineer and Full-stack / Systems developer. My main interest is building LLM-based NPC, story agent, world state, memory, and rule engine systems that can work together inside game environments.

I enjoy turning research ideas into working systems and dealing with practical constraints such as latency, consistency, reliability, and deployment. This blog is where I write about AI agents, game systems, backend operations, and research implementation.

## Current Interests

- LLM agent systems for game environments
- NPC memory, world state, event triggers, and rule engines
- Long-term memory systems based on RAG, knowledge graphs, and FAISS
- AI service operations with FastAPI, Redis, PostgreSQL, and WebSocket
- C# clients, TCP communication, UI events, and state management
- GNN, computer vision, and anomaly region detection research

## Projects

### Animus

Animus is a personal R&D project for a low-latency NPC dialogue engine based on local LLMs. It separates the LLM generation path from the player-facing response path through an Anima / Persona architecture, and experiments with response caching based on NPC_ID, Topic, and WorldHash.

The goal is not only to generate NPC dialogue, but also to keep world state changes, NPC memory, relationships, and event flow consistent over long interactions.

### WorldWeaver

WorldWeaver is an interactive story game system based on world knowledge graphs. It combines knowledge graph conversion, NPC-specific memory graphs, FAISS RAG, and a RuleEngine to manage story progression, choices, NPC conversations, quests, combat, inventory, and save/load state.

The LLM handles narration and expression, while the graph and RuleEngine are responsible for factual consistency and rule validation.

### TCP_Talk

TCP_Talk is a C# TCP chat and network protocol project. I implemented socket-based message sending and receiving, message-type handling, data parsing, connection shutdown, and exception handling.

In the GUI client, I worked with user input, button/key events, delegate/event-based state passing, and UI updates from a receiving thread. The project helped me understand how client-side input handling, state changes, rendering, and error handling should form one coherent flow.

## Experience

### OCTAGNOSIS / Korea Career Aptitude Center

Since December 2025, I have worked as a full-stack freelancer on production service improvements and AI service development.

- Built an AI analysis server with FastAPI, Gemini API, Redis, and PostgreSQL
- Operated a PDF generation server based on Node.js / Express, Playwright, and Piscina Worker Pool
- Improved and refactored a Next.js 15 admin system
- Built CI/CD with GitHub Actions, GHCR, and Docker
- Migrated a Windows Server / IIS service to AWS Lightsail Ubuntu with an Nginx Gateway
- Fixed SQL injection risks and blocked unauthorized access to test results
- Audited 20,636 records and found 39 data integrity issues
- Diagnosed PostgreSQL performance issues including duplicate indexes and temporary file usage

My work has focused on understanding existing production systems, reducing operational risk, and replacing manual patching with more reliable automation.

## Research

I received my M.S. in Information and Communication Engineering from Myongji University. My master's thesis is **Modular GNN NAC: Noise-Adaptive Correction of Graph Neural Networks Using Attention Discrepancy**.

My research background includes GNNs, computer vision, object detection, and anomaly region detection. I have published work on GAT-based noise suppression, lightweight UAV object detection, and U-ISORD anomaly region detection, and I have patent application experience in GNN-based multisensor noise/redundancy detection and unknown object detection.

Recently, I submitted **Anima/Persona: Dual-Agent NPC Dialogue** as an IEEE CoG 2026 short paper.

## Tech Stack

- **LLM / Agent**: Gemma, Gemini, LangChain LCEL, Pydantic v2, RAG, FAISS, Knowledge Graph
- **Backend / Serving**: FastAPI, WebSocket, Express, Redis, PostgreSQL, Prometheus, Grafana
- **Frontend / Client**: React, Next.js, TypeScript, Vite, C#, Unity
- **Systems / Infra**: Docker, GitHub Actions, GHCR, Nginx, AWS Lightsail, Ubuntu, Windows Server / IIS
- **Research / Data**: PyTorch Geometric, GNN, NetworkX, Computer Vision, EXPLAIN ANALYZE

## Education

- M.S. in Information and Communication Engineering, Myongji University, 2025.08
- B.S. in Computer Software, Korean Bible University, 2023.08

## Links

- GitHub: [kimhwan1103](https://github.com/kimhwan1103)
- Demo / Portfolio: [worldweaver-demo-production.up.railway.app](https://worldweaver-demo-production.up.railway.app)
- Email: [rlaghks1103@gmail.com](mailto:rlaghks1103@gmail.com)

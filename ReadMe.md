# Mungta (멍타) - Dog Walking Social Platform

<p align="center">
  <img src="./resource/MainLogo.png" alt="Mungta Logo" width="200"/>
</p>

<p align="center">
  <b>🐕 A social platform for dog owners to record, share, and connect through dog walking 🐕</b>
</p>

<p align="center">
  <a href="#english">English</a> | <a href="#korean">한국어</a>
</p>

---

<div id="english">

## 📋 Table of Contents (English)
- [Project Overview](#project-overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Installation](#installation)
- [Team Members](#team-members)
- [What I Did (bigbowltakestime)](#what-i-did)
- [Screenshots](#screenshots)

## 🎯 Project Overview

**Mungta (멍타)** is a web application designed for dog owners to:
- 🗺️ **Record and visualize** dog walking routes on an interactive map
- 🤝 **Connect with other dog owners** and make friends for their dogs
- 📊 **Manage walking records** with data visualization and calendar integration
- 🛒 **Trade second-hand pet items** through a marketplace
- 💬 **Chat** with other owners via 1:1 and group chat rooms
- 📸 **Share moments** through a social feed (Instagram-like feature for dogs)

### Project Goal
> Create an application that records dog walks, shares those records, helps dogs make friends, and manages walking data efficiently.

## ✨ Features

### Map Features (DangMap / 댕맵)
1. **Display walking routes** on map with custom markers
2. **Daily marker limit** - Restrict number of markers per day
3. **View other users' routes** - See where other dogs are walking
4. **User identification** - See who marked on the map
5. **Marker clustering** - Group dense marker areas for better visualization
6. **Weather API integration** - Display current weather information
7. **Profile preview** - Click markers to see user profiles
8. **Auto group chat creation** - Create chat rooms for popular walking spots

### Social Features (Dangstar / 댕스타)
9. **Social feed** - Post photos and updates (Instagram-like)
10. **Comments** - Write, edit, and delete comments on posts
11. **Likes** - Like posts and receive notifications
12. **Second-hand marketplace** (DangMarket / 댕댕마켓) - Buy/sell pet items with image upload

### Communication Features (DangTalk / 댕톡)
13. **1:1 Private chat** - Direct messaging between users
14. **Group chat** - Public chat rooms for popular walking areas
15. **Real-time messaging** - Instant message delivery via Socket.io

### User Features
16. **Calendar integration** - Auto-mark walking days on calendar
17. **My posts & comments** - View all your activity history
18. **Notifications** - Get alerts for chats, follows, and likes
19. **Follow system** - Follow other users and their walking routes
20. **Temperature system** - User reputation/reliability scoring
21. **Authentication** - JWT-based secure login/logout

## 🛠 Tech Stack

### Frontend
- **Vanilla JavaScript (ES6+)** - No frameworks, pure JavaScript
- **Kakao Map API** - Map visualization and geolocation
- **Weather API** - Real-time weather data

### Backend
- **Node.js** - Runtime environment
- **Native HTTP Module** - Custom server implementation (no Express)
- **Socket.io** - Real-time bidirectional communication
- **JWT (JSON Web Tokens)** - Authentication & authorization
- **busboy** - File upload handling
- **multer** - Alternative file upload support

### Database
- **MySQL** - Relational database
- **Connection pooling** - Efficient database connections

### Development Tools
- **ES Modules** - Modern JavaScript module system
- **Git** - Version control

## 🏗 Architecture

### Project Structure
```
Mungta/
├── app.js                      # Main server entry point (Port 2080)
├── package.json                # Dependencies and scripts
├── mungta.sql                  # Complete database schema
│
├── backEnd/                    # Backend modules
│   ├── Router/                 # API route handlers
│   │   ├── home/               # Home page routes
│   │   ├── login/              # Authentication (JWT)
│   │   ├── Map/                # DangMap functionality
│   │   ├── PostBoard/          # Dangstar & DangMarket
│   │   ├── chat/               # DangTalk messaging
│   │   ├── profile/            # User profiles
│   │   ├── social/             # Friend system
│   │   └── alarm/              # Notifications
│   ├── module/                 # Utility modules
│   │   ├── dangtalkSocketIo.js # Chat socket handler
│   │   ├── imageUpload.js      # Image processing
│   │   ├── jsonWebToken.js     # JWT utilities
│   │   └── followSearch.js     # Follow system
│   └── fileReader/             # Static file serving
│
├── frontEnd/                   # Frontend JavaScript
│   ├── Home/                   # Home page & weather
│   ├── dangMap/                # Map interaction
│   ├── dangtalk/               # Chat interface
│   ├── postBoard/              # Social feed UI
│   ├── profile/                # Profile pages
│   ├── dangfriends/            # Friend list
│   └── login/                  # Auth pages
│
├── common/                     # Shared components
│   ├── htmlBox.js              # HTML templates
│   ├── topMenu.js              # Navigation
│   ├── bottomMenu.js           # Footer navigation
│   └── commonStyle.js          # Shared styles
│
├── graphic/                    # Weather icons & graphics
├── image/                      # User uploaded images
├── resource/                   # Static resources
└── friends/                    # Friend page components
```

### Database Schema

#### Core Tables
- **`userinfo`** - User accounts (id, password, dog info, security questions)
- **`map_tables`** - Walking markers (latitude, longitude, timestamp, user_id)
- **`dangstar`** - Social posts (content, images, likes, timestamps)
- **`dangmarket`** - Marketplace listings

#### Social Tables
- **`dangstar_comment`** - Post comments
- **`dangstar_like`** - Post likes
- **`fr_list`** - Friend/follow relationships
- **`star_check`** - Favorite/starred markers

#### Communication Tables
- **`chat_room`** - Chat room memberships
- **`chat_text`** - Chat messages
- **`alarm`** - Notifications (likes, follows, comments, chat invites)

#### User Data Tables
- **`temperature`** - User reputation scores

## 🚀 Installation

### Prerequisites
- Node.js (v14 or higher)
- MySQL (v8.0 or higher)
- npm or yarn

### Step 1: Clone the Repository
```bash
git clone https://github.com/kongukjae/KDT-2-Project-C-3.git
cd KDT-2-Project-C-3
```

### Step 2: Install Dependencies
```bash
npm install
```

### Step 3: Database Setup
1. Start MySQL server
2. Create database:
```sql
CREATE DATABASE mungta;
```
3. Import schema:
```bash
mysql -u root -p mungta < mungta.sql
```

### Step 4: Configure Database Connection
Edit `backEnd/commonServer.js` or database configuration files:
```javascript
const mysqlInfo = {
  host: "localhost",  // or "192.168.100.63" for server
  user: "guest",
  password: "0000",
  database: "mungta"
};
```

### Step 5: Start the Server
```bash
node app.js
```

Server will run on `http://localhost:2080`

### Step 6: Access the Application
Open your browser and navigate to:
```
http://localhost:2080
```

## 👥 Team Members

| Role | Name | GitHub |
|------|------|--------|
| **Team Leader** | 류은이 (Ryu Euni) | - |
| **Backend Developer** | 김종윤 (Kim Jongyoon) | kimjongyoon96 |
| **Frontend Developer** | 김지섭 (Kim Jiseop) | JseopKim |
| **Full-stack Developer** | 김형진 (Kim Hyungjin) | bigbowltakestime |
| **Backend Developer** | 노수민 (No Sumin) | - |

**Team Name**: C3 IZ*ONE (KDT 2nd Generation Project)

## 🏆 What I Did (bigbowltakestime)

As **Kim Hyungjin (김형진)** with GitHub ID **bigbowltakestime**, I contributed extensively to the Mungta project with over **247+ commits** across the development period.

### Key Contributions

#### 🗄️ Database Management
- Designed and optimized the **MySQL database schema** (`mungta.sql`)
- Implemented efficient queries for map marker retrieval
- Managed database connections and query optimization
- Created complex JOIN queries for friend-based marker filtering

#### 🗺️ DangMap (Map Feature) Backend
- Developed **map data API endpoints** (`dangmap_read_get.js`)
- Implemented marker categorization:
  - **My Markers** (`/loadMap`) - User's own walking routes
  - **Starred/Favorite Markers** (`/starFootprint`) - Followed users with star
  - **Friend Markers** (`/frFootprint`) - Regular friends' routes
  - **Other Users** (`/otFootprint`) - Public routes from non-friends
- Created calendar-based marker loading (`/allloadMap`)
- Implemented marker clustering logic

#### 📱 Dangstar (Social Feed) Backend
- Built **social feed API** (`dangstarGet.js`)
- Implemented **infinite scroll pagination** with `limit` and `offset`
- Created post loading with chronological ordering

#### 💬 Chat System
- Developed **public chat room generation** system (`dangmapPublicChatGenerator.js`)
- Implemented location-based chat room creation
- Created chat list management and participant tracking

#### 👥 Social Features
- Implemented **follow system** (`followSearch.js`)
- Created friend relationship management
- Developed user search functionality

#### 🖼️ Image Handling
- Built **image upload module** (`imageUpload.js`)
- Implemented file processing with busboy
- Created image storage and retrieval system

#### 🔧 Infrastructure & DevOps
- **Server deployment** configuration and management
- **Code cleanup** and refactoring for maintainability
- **Bug fixes** across multiple modules
- **Merge request management** (30+ PRs reviewed and merged)

### Technical Skills Demonstrated
- **Backend Architecture**: RESTful API design with native Node.js HTTP module
- **Database Design**: Complex SQL queries, indexing, relationship management
- **Real-time Communication**: Socket.io integration for chat features
- **File Processing**: Image upload handling and storage
- **Version Control**: Git workflow management, conflict resolution
- **Code Quality**: Refactoring, optimization, documentation

### Notable Issues Resolved
- Issue #188 - Various feature implementations
- Issue #273 - Bug fixes and optimizations
- Issue #305 - Database and server improvements
- Issue #315 - Server deployment configuration

---

</div>

<div id="korean">

## 📋 목차 (한국어)
- [프로젝트 개요](#프로젝트-개요)
- [주요 기능](#주요-기능)
- [기술 스택](#기술-스택)
- [시스템 구조](#시스템-구조)
- [설치 방법](#설치-방법)
- [팀원 소개](#팀원-소개)
- [내가 한 일 (bigbowltakestime)](#내가-한-일)
- [스크린샷](#스크린샷)

## 🎯 프로젝트 개요

**멍타(Mungta)**는 반려견 주인들을 위한 웹 애플리케이션입니다:
- 🗺️ **산책 경로 기록 및 시각화** - 인터랙티브 지도에서 산책로 표시
- 🤝 **다른 반려견 주인과 연결** - 강아지 친구 만들기
- 📊 **산책 기록 관리** - 데이터 시각화와 캘린더 연동
- 🛒 **중고 거래** - 반려동물 용품 거래 마켓플레이스
- 💬 **채팅 기능** - 1:1 및 단체 채팅방
- 📸 **순간 공유** - 인스타그램 스타일의 소셜 피드

### 프로젝트 목표
> 강아지의 산책을 기록하고, 그 기록을 공유하며 강아지의 친구를 만들어주고, 산책 기록을 데이터화하여 관리할 수 있는 어플리케이션 제작

## ✨ 주요 기능

### 지도 기능 (댕맵)
1. **산책 경로 표시** - 지도에 커스텀 마커로 경로 표시
2. **일일 마커 제한** - 하루에 찍을 수 있는 마커 개수 제한
3. **다른 사용자 경로 보기** - 다른 강아지들의 산책로 확인
4. **사용자 식별** - 지도에 표시된 사람들이 누구인지 확인
5. **마커 클러스터링** - 밀집된 마커 영역 그룹화
6. **날씨 API 연동** - 실시간 날씨 정보 표시
7. **프로필 미리보기** - 마커 클릭으로 사용자 프로필 확인
8. **자동 단체 채팅방 생성** - 인기 산책 장소에 채팅방 자동 생성

### 소셜 기능 (댕스타)
9. **소셜 피드** - 사진과 업데이트 게시 (인스타그램 스타일)
10. **댓글 기능** - 게시글에 댓글 작성, 수정, 삭제
11. **좋아요** - 게시글 좋아요 및 알림 수신
12. **중고거래 마켓** (댕댕마켓) - 이미지 업로드로 반려용품 거래

### 커뮤니케이션 기능 (댕톡)
13. **1:1 개인 채팅** - 사용자 간 직접 메시지
14. **단체 채팅** - 인기 산책 지역의 공개 채팅방
15. **실시간 메시징** - Socket.io로 즉각적인 메시지 전달

### 사용자 기능
16. **캘린더 연동** - 산책한 날짜를 캘린더에 자동 표시
17. **내 게시글 및 댓글** - 모든 활동 내역 확인
18. **알림 기능** - 채팅, 팔로우, 좋아요 알림
19. **팔로우 시스템** - 다른 사용자 팔로우 및 산책로 확인
20. **산책 온도 시스템** - 사용자 신뢰도/평판 점수
21. **인증 시스템** - JWT 기반 보안 로그인/로그아웃

## 🛠 기술 스택

### 프론트엔드
- **Vanilla JavaScript (ES6+)** - 프레임워크 없는 순수 JavaScript
- **Kakao Map API** - 지도 시각화 및 위치 정보
- **Weather API** - 실시간 날씨 데이터

### 백엔드
- **Node.js** - 런타임 환경
- **Native HTTP Module** - Express 없는 커스텀 서버 구현
- **Socket.io** - 실시간 양방향 통신
- **JWT (JSON Web Tokens)** - 인증 및 권한 부여
- **busboy** - 파일 업로드 처리
- **multer** - 대체 파일 업로드 지원

### 데이터베이스
- **MySQL** - 관계형 데이터베이스
- **Connection pooling** - 효율적인 데이터베이스 연결

### 개발 도구
- **ES Modules** - 현대적 JavaScript 모듈 시스템
- **Git** - 버전 관리

## 🏗 시스템 구조

### 프로젝트 구조
```
Mungta/
├── app.js                      # 메인 서버 진입점 (포트 2080)
├── package.json                # 의존성 및 스크립트
├── mungta.sql                  # 완전한 데이터베이스 스키마
│
├── backEnd/                    # 백엔드 모듈
│   ├── Router/                 # API 라우트 핸들러
│   │   ├── home/               # 홈 페이지 라우트
│   │   ├── login/              # 인증 (JWT)
│   │   ├── Map/                # 댕맵 기능
│   │   ├── PostBoard/          # 댕스타 & 댕댕마켓
│   │   ├── chat/               # 댕톡 메시징
│   │   ├── profile/            # 사용자 프로필
│   │   ├── social/             # 친구 시스템
│   │   └── alarm/              # 알림
│   ├── module/                 # 유틸리티 모듈
│   │   ├── dangtalkSocketIo.js # 채팅 소켓 핸들러
│   │   ├── imageUpload.js      # 이미지 처리
│   │   ├── jsonWebToken.js     # JWT 유틸리티
│   │   └── followSearch.js     # 팔로우 시스템
│   └── fileReader/             # 정적 파일 서빙
│
├── frontEnd/                   # 프론트엔드 JavaScript
│   ├── Home/                   # 홈 페이지 & 날씨
│   ├── dangMap/                # 지도 상호작용
│   ├── dangtalk/               # 채팅 인터페이스
│   ├── postBoard/              # 소셜 피드 UI
│   ├── profile/                # 프로필 페이지
│   ├── dangfriends/            # 친구 목록
│   └── login/                  # 인증 페이지
│
├── common/                     # 공유 컴포넌트
│   ├── htmlBox.js              # HTML 템플릿
│   ├── topMenu.js              # 네비게이션
│   ├── bottomMenu.js           # 하단 네비게이션
│   └── commonStyle.js          # 공유 스타일
│
├── graphic/                    # 날씨 아이콘 및 그래픽
├── image/                      # 사용자 업로드 이미지
├── resource/                   # 정적 리소스
└── friends/                    # 친구 페이지 컴포넌트
```

### 데이터베이스 스키마

#### 핵심 테이블
- **`userinfo`** - 사용자 계정 (id, 비밀번호, 강아지 정보, 보안 질문)
- **`map_tables`** - 산책 마커 (위도, 경도, 타임스탬프, user_id)
- **`dangstar`** - 소셜 게시글 (내용, 이미지, 좋아요, 타임스탬프)
- **`dangmarket`** - 마켓플레이스 목록

#### 소셜 테이블
- **`dangstar_comment`** - 게시글 댓글
- **`dangstar_like`** - 게시글 좋아요
- **`fr_list`** - 친구/팔로우 관계
- **`star_check`** - 즐겨찾기/별표 마커

#### 커뮤니케이션 테이블
- **`chat_room`** - 채팅방 멤버십
- **`chat_text`** - 채팅 메시지
- **`alarm`** - 알림 (좋아요, 팔로우, 댓글, 채팅 초대)

#### 사용자 데이터 테이블
- **`temperature`** - 사용자 평판 점수

## 🚀 설치 방법

### 필수 조건
- Node.js (v14 이상)
- MySQL (v8.0 이상)
- npm 또는 yarn

### 1단계: 저장소 클론
```bash
git clone https://github.com/kongukjae/KDT-2-Project-C-3.git
cd KDT-2-Project-C-3
```

### 2단계: 의존성 설치
```bash
npm install
```

### 3단계: 데이터베이스 설정
1. MySQL 서버 시작
2. 데이터베이스 생성:
```sql
CREATE DATABASE mungta;
```
3. 스키마 임포트:
```bash
mysql -u root -p mungta < mungta.sql
```

### 4단계: 데이터베이스 연결 설정
`backEnd/commonServer.js` 또는 데이터베이스 설정 파일 편집:
```javascript
const mysqlInfo = {
  host: "localhost",  // 또는 서버용 "192.168.100.63"
  user: "guest",
  password: "0000",
  database: "mungta"
};
```

### 5단계: 서버 시작
```bash
node app.js
```

서버가 `http://localhost:2080`에서 실행됩니다

### 6단계: 애플리케이션 접속
브라우저에서 다음 주소로 접속:
```
http://localhost:2080
```

## 👥 팀원 소개

| 역할 | 이름 | GitHub |
|------|------|--------|
| **팀장** | 류은이 | - |
| **백엔드 개발자** | 김종윤 | kimjongyoon96 |
| **프론트엔드 개발자** | 김지섭 | JseopKim |
| **풀스택 개발자** | 김형진 | bigbowltakestime |
| **백엔드 개발자** | 노수민 | - |

**팀명**: C3 아이즈원 (KDT 2기 프로젝트)

## 🏆 내가 한 일 (bigbowltakestime)

**김형진**으로서 GitHub ID **bigbowltakestime**으로 멍타 프로젝트에 **247개 이상의 커밋**을 기여했습니다.

### 주요 기여사항

#### 🗄️ 데이터베이스 관리
- **MySQL 데이터베이스 스키마** 설계 및 최적화 (`mungta.sql`)
- 지도 마커 검색을 위한 효율적인 쿼리 구현
- 데이터베이스 연결 및 쿼리 최적화 관리
- 친구 기반 마커 필터링을 위한 복잡한 JOIN 쿼리 생성

#### 🗺️ 댕맵 (지도 기능) 백엔드
- **지도 데이터 API 엔드포인트** 개발 (`dangmap_read_get.js`)
- 마커 분류 구현:
  - **내 마커** (`/loadMap`) - 사용자 자신의 산책 경로
  - **즐겨찾기 마커** (`/starFootprint`) - 별표 표시된 팔로우 사용자
  - **친구 마커** (`/frFootprint`) - 일반 친구들의 경로
  - **다른 사용자** (`/otFootprint`) - 비친구의 공개 경로
- 캘린더 기반 마커 로딩 구현 (`/allloadMap`)
- 마커 클러스터링 로직 구현

#### 📱 댕스타 (소셜 피드) 백엔드
- **소셜 피드 API** 구축 (`dangstarGet.js`)
- **`limit`와 `offset`을 활용한 무한 스크롤 페이징** 구현
- 시간순 정렬로 게시글 로딩 생성

#### 💬 채팅 시스템
- **공개 채팅방 생성** 시스템 개발 (`dangmapPublicChatGenerator.js`)
- 위치 기반 채팅방 생성 구현
- 채팅 목록 관리 및 참가자 추적 생성

#### 👥 소셜 기능
- **팔로우 시스템** 구현 (`followSearch.js`)
- 친구 관계 관리 생성
- 사용자 검색 기능 개발

#### 🖼️ 이미지 처리
- **이미지 업로드 모듈** 구축 (`imageUpload.js`)
- busboy를 활용한 파일 처리 구현
- 이미지 저장 및 검색 시스템 생성

#### 🔧 인프라 및 DevOps
- **서버 배포** 설정 및 관리
- 유지보수를 위한 **코드 정리** 및 리팩토링
- 여러 모듈에서 **버그 수정**
- **머지 리퀘스트 관리** (30개 이상의 PR 검토 및 머지)

### 활용한 기술 스킬
- **백엔드 아키텍처**: 네이티브 Node.js HTTP 모듈로 RESTful API 설계
- **데이터베이스 설계**: 복잡한 SQL 쿼리, 인덱싱, 관계 관리
- **실시간 통신**: 채팅 기능을 위한 Socket.io 통합
- **파일 처리**: 이미지 업로드 처리 및 저장
- **버전 관리**: Git 워크플로우 관리, 충돌 해결
- **코드 품질**: 리팩토링, 최적화, 문서화

### 해결한 주요 이슈
- Issue #188 - 다양한 기능 구현
- Issue #273 - 버그 수정 및 최적화
- Issue #305 - 데이터베이스 및 서버 개선
- Issue #315 - 서버 배포 설정

</div>

---

## 📸 Screenshots

<div align="center">

### Login & Home
<img src="https://user-images.githubusercontent.com/117888227/227817898-a9a53503-9931-4b02-bd13-4b594eed3315.png" height="350">
<img src="https://user-images.githubusercontent.com/117888227/227817906-d499a4b7-d7ae-4ed0-982c-594fcd1a5e8f.png" height="350">

### Map Features
<img src="https://user-images.githubusercontent.com/117888227/236104178-ff9a14fd-85c8-4a6b-9988-968b837582e0.png" height="350">
<img src="https://user-images.githubusercontent.com/117888227/236104183-fe42a85f-8df9-44a7-af18-c7da9eb44bdf.png" height="350">

### Social Feed & Chat
<img src="https://user-images.githubusercontent.com/117888227/236104240-ffdcbfd5-22f3-45fc-a3c5-3ec3935f7892.png" height="350">
<img src="https://user-images.githubusercontent.com/117888227/236104253-bbe71c4b-aca8-44ac-b097-be212b1f0e03.png" height="350">

### Profile & Marketplace
<img src="https://github.com/kongukjae/KDT-2-Project-C-3/assets/117888227/e41b2a51-8333-4b38-9b6a-e714a057b220.png" height="350">
<img src="https://github.com/kongukjae/KDT-2-Project-C-3/assets/117888227/e07a2b2f-3ed0-45d3-9709-4b2f65f3ee07.png" height="350">

### Additional Features
<img src="https://user-images.githubusercontent.com/117888227/236104335-5118876f-c60d-407c-acbd-7657f633a570.png" height="350">
<img src="https://user-images.githubusercontent.com/117888227/236104339-03391004-cba5-4298-9ecd-2bcac74ffb04.png" height="350">

</div>

---

## 📄 License

This project was developed as part of the **KDT (K-Digital Training) 2nd Generation** program.

## 🙏 Acknowledgments

- **KDT Program** - For providing the learning opportunity
- **Team C3 IZ*ONE** - All team members for their hard work and collaboration
- **Kakao** - For the Map API
- **All testers and users** - For feedback and support

---

<p align="center">
  <b>🐕 Made with love for dogs and their owners 🐕</b>
</p>

<p align="center">
  <b>© 2023 Team C3 IZ*ONE - Mungta Project</b>
</p>

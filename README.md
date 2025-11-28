# Sori(소리) AI

> AI가 매일 어르신께 전화를 걸어 안부를 묻고, 보호자에게 리포트로 전달하는 케어 서비스

## Links

| 구분          | 설명                      | URL                                                      |
| ------------- | ------------------------- | -------------------------------------------------------- |
| 🌐 **Web**    | 보호자용 대시보드         | https://sori-ai.vercel.app/                              |
| 🔗 **API**    | Server API 문서 (Swagger) | https://aicarecall-server-production.up.railway.app/docs |
| 📦 **GitHub** | Web Repository            | https://github.com/codyssey-PRISM/AICareCall-web         |
| 📦 **GitHub** | Server Repository         | https://github.com/codyssey-PRISM/AICareCall-server      |
| 📦 **GitHub** | iOS Repository            | https://github.com/codyssey-PRISM/AICareCall-mobile      |

---

## 소개

<!-- 서비스 소개 및 배경 작성 -->

---

## 시스템 아키텍처

<!-- 아키텍처 다이어그램 설명 -->

![아키텍처 다이어그램](아키택처%20다이어그램.png)

---

## 기술 스택

### iOS

- **Swift / SwiftUI**
- **TCA (The Composable Architecture) 1.23.1**
- **CallKit / PushKit** - VoIP 푸시 및 시스템 전화 UI
- **Vapi iOS SDK** - AI 음성 통화

### Server

- **Python 3.13 / FastAPI**
- **SQLAlchemy / PostgreSQL**
- **APNs (HTTP/2)** - iOS 푸시 알림
- **APScheduler** - 예약 통화 스케줄러
- **Vapi Server SDK** - AI 음성 통화 연동
- **SendGrid** - 이메일 인증

### Web

- **Next.js 16 / React 19**
- **TypeScript**
- **Tailwind CSS**
- **Radix UI**
- **Zustand** - 상태 관리

---

## 프로젝트 구조

### ios/

```
CallClient/
├── CallClient/
│   ├── Dependencies/       # TCA 의존성 클라이언트
│   │   ├── APIClient/      # 서버 API 통신
│   │   ├── CallKitClient/  # CallKit 관리
│   │   ├── VapiClient/     # Vapi SDK 래핑
│   │   └── VoIPTokenClient/
│   ├── Features/           # TCA 기반 화면 기능
│   │   ├── Splash/
│   │   ├── Invitation/     # 초대 코드 입력
│   │   ├── Home/           # 메인 화면
│   │   └── Call/           # 통화 화면
│   └── Models/
```

<!-- iOS 앱 상세 구조 및 설명 작성 -->

### server/

```
app/
├── routers/           # API 엔드포인트
│   ├── auth.py       # 이메일 인증
│   ├── elders.py     # 어르신 관리
│   ├── elder_app.py  # iOS 앱용 API
│   ├── push.py       # VoIP 푸시
│   ├── webhook.py    # Vapi 웹훅
│   └── dashboard.py  # 대시보드 데이터
├── services/          # 비즈니스 로직
├── db/models/         # SQLAlchemy 모델
├── scheduler/         # 예약 통화 스케줄러
└── main.py
```

<!-- 서버 상세 구조 및 설명 작성 -->

### web/

```
app/
├── (dashboard)/       # 대시보드 레이아웃
│   ├── chat/
│   ├── report/
│   └── settings/
├── dashboard/[elderId]/ # 어르신별 대시보드
├── call-list/         # 통화 기록
├── onboarding/        # 어르신 등록 플로우
├── register/          # 회원가입
└── components/
    └── custom/        # 커스텀 컴포넌트
```

<!-- 웹 상세 구조 및 설명 작성 -->

---

## 주요 기능

### 보호자 (Web)

<!-- 주요 기능 상세 설명 -->

### 어르신 (iOS)

<!-- 주요 기능 상세 설명 -->

### 시스템 (Server)

<!-- 주요 기능 상세 설명 -->

---

## 로컬 개발 환경

### iOS

**요구사항:**

- Xcode 15+
- iOS 15+ 실기기 (시뮬레이터는 VoIP 푸시 미지원)

**설정:**

<!-- iOS 개발 환경 설정 단계 작성 -->

### Server

**요구사항:**

- Python 3.13+
- PostgreSQL (or SQLite for development)

**설정:**

```bash
# 가상환경 생성 (예: conda)
conda create -n push python=3.13
conda activate push

# 의존성 설치
pip install -r requirements.txt

# 환경변수 설정
# .env 파일 생성 및 필요한 값 설정
# - DATABASE_URL
# - APNS 관련 설정 (TEAM_ID, KEY_ID, BUNDLE_ID, P8_PRIVATE_KEY_PATH)
# - SENDGRID_API_KEY
# - VAPI_API_KEY

# DB 마이그레이션
alembic upgrade head

# 서버 실행
uvicorn app.main:app --reload
```

<!-- 추가 설정 및 주의사항 작성 -->

### Web

**요구사항:**

- Node.js 18+
- npm or pnpm

**설정:**

```bash
# 의존성 설치
npm install

# 환경변수 설정
# .env.local 파일 생성
# NEXT_PUBLIC_API_URL=http://localhost:8000

# 개발 서버 실행
npm run dev
```

<!-- 추가 설정 및 주의사항 작성 -->

---

## 팀

<!-- 팀 정보 및 기여자 작성 -->

---

## 라이선스

<!-- 라이선스 정보 작성 -->

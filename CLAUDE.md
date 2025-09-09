# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Japan travel expense tracking application project. The codebase is currently empty and awaiting initial setup.

## Development Setup

### Git Repository
- Repository: https://github.com/kimyeonghoon/JAPAN_TRAVEL_EXPENSE.git
- Main branch: `main`
- Git user configured as: 김영훈 <me@yeonghoon.kim>

### Technology Stack
- **Backend**: Python FastAPI
- **Frontend**: HTML/CSS/JavaScript with jQuery and Bootstrap 5
- **Styling**: Bootstrap 5 + Custom CSS
- **Data Storage**: SQLite database with persistent volume
- **Deployment**: Docker Compose ready

### Development Commands
```bash
# Install Python dependencies
pip install -r requirements.txt

# Run development server
python main.py
# or
uvicorn main:app --reload

# Access application
# Frontend: http://localhost:8000
# API docs: http://localhost:8000/docs
```

### Docker Deployment

#### 🚀 배포 가이드

**1. 저장소 클론 및 이동**
```bash
git clone https://github.com/kimyeonghoon/JAPAN_TRAVEL_EXPENSE.git
cd JAPAN_TRAVEL_EXPENSE
```

**2. Docker Compose로 배포**
```bash
# 이미지 빌드 후 실행 (최초 실행)
docker-compose up --build

# 백그라운드에서 실행
docker-compose up -d

# 서비스 중지
docker-compose down

# 로그 확인
docker-compose logs -f

# 변경사항 반영하여 재배포
docker-compose up --build --force-recreate
```

**3. 서비스 관리**
```bash
# 컨테이너 상태 확인
docker-compose ps

# 헬스체크 상태 확인
docker ps --format "table {{.Names}}\t{{.Status}}"

# 컨테이너 내부 접근
docker exec -it japan-travel-expense bash

# 데이터베이스 직접 접근
docker exec -it japan-travel-expense sqlite3 /app/data/japan_travel_expenses.db
```

**4. 데이터 백업**
```bash
# SQLite 데이터베이스 백업
cp ./data/japan_travel_expenses.db ./backup/japan_travel_expenses_$(date +%Y%m%d_%H%M%S).db
```

#### 📋 배포 전 체크리스트
- [ ] Docker 및 Docker Compose 설치 확인
- [ ] 포트 8000번 사용 가능 여부 확인
- [ ] 충분한 디스크 공간 확보 (최소 500MB)
- [ ] 방화벽 설정 (필요시 8000번 포트 개방)

#### 🔧 문제해결
- **포트 충돌**: `docker-compose.yml`에서 포트 변경 (예: 8080:8000)
- **권한 문제**: `sudo` 권한으로 Docker 명령어 실행
- **헬스체크 실패**: 로그 확인 후 `/api/health` 엔드포인트 접근 테스트

### Common Git Commands
```bash
git status                  # Check repository status
git add .                   # Stage all changes
git commit -m "message"     # Commit changes
git push origin main        # Push to GitHub
git pull origin main        # Pull latest changes
```

## Project Structure

```
japan_travel_expense/
├── main.py                 # FastAPI main application
├── models.py              # SQLAlchemy database models
├── database.py            # Database service layer
├── requirements.txt        # Python dependencies
├── Dockerfile             # Docker container configuration
├── docker-compose.yml     # Docker Compose setup
├── .dockerignore          # Docker ignore file
├── templates/
│   └── index.html         # Main HTML template
├── static/
│   ├── css/
│   │   └── style.css      # Custom styles
│   └── js/
│       └── app.js         # jQuery application logic
├── data/                  # SQLite database directory (Docker volume)
└── .claude/               # Claude Code configuration
```

## Architecture

- **Frontend**: Single-page application using jQuery and Bootstrap
- **Backend**: FastAPI serves templates and provides REST API endpoints
- **Database**: SQLite with SQLAlchemy ORM for data persistence
- **Container**: Docker with persistent volume for database storage
- **Responsive Design**: Mobile-first approach with Bootstrap grid system

## Current Status

- ✅ Git repository initialized and connected to GitHub
- ✅ Technology stack configured (FastAPI + jQuery + Bootstrap + SQLite)
- ✅ Project structure created with all necessary files
- ✅ Frontend UI implemented with mobile responsive design
- ✅ Complete REST API implementation with database integration
- ✅ SQLite database with SQLAlchemy ORM
- ✅ Docker containerization with Docker Compose
- ✅ Production-ready deployment configuration

## Notes

- Project directory: `C:\workspace\japan_travel_expense`
- Repository URL: https://github.com/kimyeonghoon/JAPAN_TRAVEL_EXPENSE.git
- Claude Code permissions configured for git operations
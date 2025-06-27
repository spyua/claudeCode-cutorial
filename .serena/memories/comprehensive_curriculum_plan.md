# Claude Code 三天制專業課程規劃

## 課程總覽
- **目標群體**: 有程式開發基礎的軟體工程師
- **總時數**: 24小時 (3天 × 8小時)
- **模組數**: 10個核心模組 (M0-M10)
- **實作Lab**: 12個動手實作
- **學習曲線**: 基礎 → 進階 → 實戰

## DAY 1: 基礎建設與核心概念 (8小時)
### 模組架構
- **M0**: 環境準備 (30分鐘)
- **M1**: 核心概念 (60分鐘)  
- **M2**: .claude設定 + Lab 1 (75分鐘)
- **M3**: Slash指令 + Lab 2 (90分鐘)
- **M4**: TDD + Lab 3 (90分鐘)
- **M8-1**: Memory基礎 + Lab 6 (60分鐘)

### 檢核標準
- 能獨立設定.claude專案環境
- 理解16個核心工具功能
- 知道如何建立自定義slash指令
- 會使用TDD流程開發功能
- 理解Memory管理基本概念

## DAY 2: 進階協作與安全治理 (8小時)
### 模組架構
- **M8-2,3**: Memory Imports + Lab 7 (90分鐘)
- **M5**: 團隊協作 + Lab 4 (90分鐘)
- **M8-4,5**: Memory清理 + Lab 8 (90分鐘)
- **M7**: 安全治理 + Lab 9 (90分鐘)
- **M9**: Issue閉環 + Lab 10 (60分鐘)

### 檢核標準
- 能設計檔案匯入策略
- 會使用Worktree進行並行開發
- 掌握Memory清理最佳實務
- 建立完整安全防護機制
- 整合GitHub Issue工作流

## DAY 3: 實戰專案與企業應用 (8小時)
### 模組架構
- **M6**: CI/CD + Lab 5 (90分鐘)
- **M10-1**: 後端API + Lab 11 (90分鐘)  
- **M10-2**: 前端整合 + Lab 12 (90分鐘)
- **全端部署實戰** (90分鐘)

### 檢核標準
- 建立完整CI/CD流程
- 開發全端Todo應用
- 實現自動化部署
- 具備獨立專案開發能力

## 技術棧規格
### 後端技術
- Spring Boot 3.2+, Java 17+
- Spring Data JPA, H2/PostgreSQL
- JUnit 5 + Testcontainers

### 前端技術
- React 18, TypeScript 5+
- Vite 5, React Query
- Playwright (E2E測試)

### DevOps技術
- Docker & Docker Compose
- GitHub Actions, Kubernetes
- Prometheus + Grafana
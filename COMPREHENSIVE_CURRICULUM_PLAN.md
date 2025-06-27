# 🎓 Claude Code 三天制專業課程規劃計畫

## 📋 執行檔案說明

**本檔案作為 Serena/Cursor Agent 的執行藍圖**

此計畫整合了官方文檔技術分析與教學經驗，提供完整的課程開發指導。Serena/Cursor Agent 可依據此規劃自動生成詳細的課程內容、Lab 操作手冊、以及教學資源。

---

## 🎯 課程總覽

### 核心定位
- **目標群體**: 有程式開發基礎的軟體工程師
- **學習目標**: 掌握 Claude Code 從基礎操作到企業級應用的完整技能
- **課程特色**: 實作導向、記憶體管理意識、安全優先、團隊協作

### 課程架構
```
三天制課程 (總計 24 小時)
├── Day 1: 基礎建設與核心概念 (8小時)
├── Day 2: 進階協作與安全治理 (8小時)
└── Day 3: 實戰專案與企業應用 (8小時)
```

---

## 📅 DAY 1: 基礎建設與核心概念

### 🎯 學習目標
學員能夠獨立設定 Claude Code 環境，理解核心概念，並建立基本的開發工作流程。

### 📚 模組規劃

#### **M0: 環境準備與安裝 (30分鐘)**
**內容重點:**
- Claude Code 安裝與身份驗證
- 系統需求檢查與故障排除
- 基本命令列操作

**技術細節:**
```bash
# 安裝檢查清單
- Node.js 18+ ✓
- Git 2.23+ ✓
- 網路連接 ✓
- npm install -g @anthropic-ai/claude-code ✓
```

**交付物:**
- 環境設定檢核表
- 常見安裝問題解決方案

#### **M1: 核心概念深度解析 (60分鐘)**
**內容重點:**
- Claude Code 架構與工作原理
- 16 個核心工具功能介紹
- 權限系統與安全機制
- 互動模式與命令結構

**技術細節:**
```typescript
// 核心工具分類
檔案操作: Read, Write, Edit, MultiEdit, Glob, LS
執行環境: Bash
程式分析: Grep
專案管理: TodoRead, TodoWrite
網路功能: WebFetch, WebSearch
IDE整合: NotebookRead, NotebookEdit
工作流程: Agent
```

**交付物:**
- 核心概念圖解
- 工具功能對照表

#### **M2: .claude 專案設定 + Lab 1 (75分鐘)**
**內容重點:**
- CLAUDE.md 檔案結構與最佳實踐
- 三層記憶體架構設計
- 專案特定設定策略

**Lab 1: 完整的 .claude 目錄設定**
```
.claude/
├── CLAUDE.md              # 專案核心說明
├── settings.json          # 基本配置
├── commands/              # 自定義指令
│   ├── backend.md
│   ├── frontend.md
│   └── tdd.md
├── templates/             # 程式碼範本
└── memory-diet-checklist.md
```

**交付物:**
- .claude 目錄完整範本
- 記憶體管理檢核表

#### **M3: Slash 指令系統 + Lab 2 (90分鐘)**
**內容重點:**
- 自定義 Slash 指令開發
- $ARGUMENTS 參數系統
- 指令鏈結與組合

**Lab 2: 後端 API 開發指令系統**
```markdown
# .claude/commands/api-dev.md
請為 $ARGUMENTS API 端點執行完整開發流程：

1. 設計 API 規格
2. 實作控制器
3. 建立測試案例
4. 驗證功能完整性
5. 產出 API 文件
```

**交付物:**
- 完整的指令庫範本
- 指令開發最佳實踐

#### **M4: 測試驅動開發 + Lab 3 (90分鐘)**
**內容重點:**
- TDD 工作流程與 Claude Code 整合
- 測試先行的開發模式
- 測試框架整合策略

**Lab 3: TDD 任務管理器實作**
```javascript
// 測試驅動開發實作流程
1. 撰寫失敗測試
2. 執行測試確認失敗
3. 實作最小功能代碼
4. 執行測試確認通過
5. 重構優化代碼
```

**交付物:**
- TDD 工作流程模板
- 測試驅動開發範例專案

#### **M8-1: Memory 基礎管理 + Lab 6 (60分鐘)**
**內容重點:**
- 上下文管理策略
- 記憶體使用監控
- 效能優化技巧

**Lab 6: 記憶體監控工具**
```bash
# 記憶體監控指令
/memory-status    # 顯示當前記憶體使用
/memory-clean     # 清理不必要內容
/memory-optimize  # 優化記憶體結構
```

**交付物:**
- 記憶體監控儀表板
- 優化建議報告

### 📊 Day 1 檢核標準
```
□ 能獨立設定 .claude 專案環境
□ 理解 16 個核心工具功能
□ 知道如何建立自定義 slash 指令
□ 會使用 TDD 流程開發功能
□ 理解 Memory 管理基本概念
□ 完成 4 個實作 Lab
```

---

## 📅 DAY 2: 進階協作與安全治理

### 🎯 學習目標
學員能夠在團隊環境中有效使用 Claude Code，建立安全的開發流程，並掌握進階記憶體管理技巧。

### 📚 模組規劃

#### **M8-2,3: Memory 檔案匯入 + Lab 7 (90分鐘)**
**內容重點:**
- @ 符號檔案參考系統
- 動態記憶體匯入策略
- 大型專案記憶體管理

**Lab 7: 檔案匯入策略系統**
```markdown
# Memory 匯入策略
@README.md 專案概覽
@package.json 可用命令
@docs/api.md API 規格
@src/types.ts 型別定義
```

**技術細節:**
```typescript
// 匯入優先順序
1. 核心配置檔案 (package.json, tsconfig.json)
2. 專案文檔 (README.md, API docs)
3. 型別定義檔案 (.d.ts, types.ts)
4. 關鍵業務邏輯檔案
```

**交付物:**
- 記憶體匯入策略範本
- 大型專案管理指南

#### **M5: 團隊協作工作流程 + Lab 4 (90分鐘)**
**內容重點:**
- Git Worktree 並行開發
- 團隊 .claude 設定共享
- 協作最佳實踐

**Lab 4: Git Worktree 協作範例**
```bash
# Worktree 協作流程
git worktree add ../feature-branch feature-branch
cd ../feature-branch
claude  # 在隔離環境中開發
```

**交付物:**
- 團隊協作工作流程指南
- Worktree 使用範例

#### **M8-4,5: Memory 清理與優化 + Lab 8 (90分鐘)**
**內容重點:**
- 記憶體清理自動化
- 效能監控與調整
- 成本控制策略

**Lab 8: 記憶體清理自動化**
```javascript
// 自動清理腳本
const memoryCleanup = {
  removeOldSessions: true,
  compactLargeFiles: true,
  optimizeFrequentlyUsed: true,
  alertThreshold: 80
};
```

**交付物:**
- 自動化清理工具
- 效能監控儀表板

#### **M7: 安全治理框架 + Lab 9 (90分鐘)**
**內容重點:**
- 權限管理最佳實踐
- 安全配置模板
- 企業級安全策略

**Lab 9: 安全配置與 Memory Linter**
```json
{
  "security": {
    "allowedTools": ["Edit", "Read", "Bash(git:*)"],
    "deniedPatterns": ["rm -rf", "sudo", "curl"],
    "auditMode": true,
    "teamPolicy": "enforce"
  }
}
```

**交付物:**
- 安全配置範本
- 安全稽核工具

#### **M9: GitHub Issue 閉環管理 + Lab 10 (60分鐘)**
**內容重點:**
- GitHub CLI 整合
- Issue 自動化流程
- PR 管理最佳實踐

**Lab 10: GitHub Issue 自動化流程**
```bash
# Issue 處理流程
gh issue view $ISSUE_ID
claude -p "Fix issue #$ISSUE_ID"
gh pr create --title "Fix #$ISSUE_ID"
```

**交付物:**
- GitHub 整合工作流程
- Issue 管理自動化腳本

### 📊 Day 2 檢核標準
```
□ 能設計檔案匯入策略
□ 會使用 Worktree 進行並行開發
□ 掌握 Memory 清理最佳實務
□ 建立完整安全防護機制
□ 整合 GitHub Issue 工作流
□ 完成 5 個進階 Lab
```

---

## 📅 DAY 3: 實戰專案與企業應用

### 🎯 學習目標
學員能夠獨立開發完整的全端應用，建立 CI/CD 流程，並具備企業級 Claude Code 應用能力。

### 📚 模組規劃

#### **M6: CI/CD 整合 + Lab 5 (90分鐘)**
**內容重點:**
- GitHub Actions 整合
- 自動化測試與部署
- 雲端平台整合 (AWS Bedrock, Google Vertex AI)

**Lab 5: 完整 CI/CD Pipeline**
```yaml
# .github/workflows/claude-ci.yml
name: Claude Code CI/CD
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  claude-review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Claude Code Review
        uses: ./.github/actions/claude-review
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
```

**交付物:**
- CI/CD 流程範本
- 雲端部署指南

#### **M10-1: 後端 API 開發 + Lab 11 (90分鐘)**
**內容重點:**
- Spring Boot 3 整合
- RESTful API 設計
- 資料庫整合與測試

**Lab 11: Spring Boot Todo API (完整 CRUD)**
```java
// Todo API 結構
@RestController
@RequestMapping("/api/todos")
public class TodoController {
    // CRUD 操作實作
    @GetMapping, @PostMapping, @PutMapping, @DeleteMapping
}
```

**技術棧:**
- Spring Boot 3.2+
- Spring Data JPA
- H2/PostgreSQL
- JUnit 5 + Testcontainers

**交付物:**
- 完整 Spring Boot 專案
- API 文檔與測試套件

#### **M10-2: 前端整合開發 + Lab 12 (90分鐘)**
**內容重點:**
- React + Vite 整合
- 前後端聯調
- E2E 測試實作

**Lab 12: React Todo 前端 (含 E2E 測試)**
```typescript
// React 專案結構
src/
├── components/
│   ├── TodoList.tsx
│   ├── TodoItem.tsx
│   └── TodoForm.tsx
├── hooks/
│   └── useTodos.ts
├── services/
│   └── api.ts
└── tests/
    └── e2e/
        └── todo.spec.ts
```

**技術棧:**
- React 18 + TypeScript
- Vite 5
- React Query
- Playwright (E2E 測試)

**交付物:**
- 完整 React 應用
- E2E 測試套件

#### **全端部署實戰 (90分鐘)**
**內容重點:**
- Docker 容器化
- Kubernetes 部署
- 監控與日誌管理

**部署架構:**
```yaml
# docker-compose.yml
version: '3.8'
services:
  frontend:
    build: ./frontend
    ports: ["3000:3000"]
  backend:
    build: ./backend
    ports: ["8080:8080"]
  database:
    image: postgres:15
    environment:
      POSTGRES_DB: todos
```

**交付物:**
- 完整部署配置
- 監控儀表板

### 📊 Day 3 檢核標準
```
□ 建立完整 CI/CD 流程
□ 開發全端 Todo 應用
□ 實現自動化部署
□ 具備獨立專案開發能力
□ 掌握企業級最佳實踐
□ 完成 3 個實戰 Lab
```

---

## 🎯 最終專案展示

### 展示架構
```
Todo 應用系統
├── 前端: React + TypeScript
├── 後端: Spring Boot + JPA
├── 資料庫: PostgreSQL
├── 部署: Docker + K8s
├── CI/CD: GitHub Actions
└── 監控: Prometheus + Grafana
```

### 評分標準 (100分)
- **功能完整性** (30分): CRUD 操作、使用者介面、錯誤處理
- **程式碼品質** (25分): 結構清晰、註解完整、遵循規範
- **測試覆蓋率** (20分): 單元測試、整合測試、E2E 測試
- **部署實作** (15分): CI/CD 流程、容器化、自動部署
- **創新應用** (10分): Claude Code 特殊用法、效率提升

---

## 📚 課程資源與支援

### 教學資源
1. **官方文檔整合**: 16 個核心工具詳細說明
2. **最佳實踐指南**: 基於官方 Best Practice 的實作建議
3. **範例程式庫**: 完整的 mini-todo-monorepo 專案
4. **故障排除手冊**: 常見問題與解決方案

### 後續支援
- 課後 Q&A 會議 (每月)
- 技術社群討論區
- 進階課程推薦
- 認證考試準備

### 擴充模組
- **企業整合**: SSO、RBAC、合規性
- **AI Agent 開發**: 進階 AI 應用
- **LLM Ops**: 大語言模型運營
- **多語言支援**: Python、Go、Rust 專案

---

## 🚀 Serena/Cursor Agent 執行指令

### 自動化產出任務
```markdown
請 Serena/Cursor Agent 依據此規劃自動產出：

1. **Day 1 詳細課程內容** (4個模組 + 4個Lab)
2. **Day 2 詳細課程內容** (4個模組 + 5個Lab)  
3. **Day 3 詳細課程內容** (3個模組 + 3個Lab)
4. **12個Lab完整操作手冊** (步驟化教學)
5. **課程資源檔案** (範本、檢核表、工具)
6. **講師教學指南** (時間控制、互動技巧)
7. **學員評估表** (知識檢核、技能驗證)
```

### 品質要求
- 每個 Lab 必須包含詳細的步驟指引
- 所有程式碼範例必須可執行
- 提供完整的錯誤處理與故障排除
- 符合官方 Best Practice 標準
- 包含實際業務場景應用

### 技術規格
- 遵循 Claude Code 官方 API 規範
- 整合 16 個核心工具的使用
- 涵蓋完整的 Memory 管理策略
- 實作企業級安全與治理框架
- 支援多種部署環境與 CI/CD 流程

---

**此課程規劃已準備完成，可立即開始執行產出！**
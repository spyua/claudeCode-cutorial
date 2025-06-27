# 🤖 SERENA/CURSOR AGENT 執行計畫

## 📋 執行任務總覽

基於 `COMPREHENSIVE_CURRICULUM_PLAN.md` 的詳細規劃，請自動產出完整的 Claude Code 三天制課程內容。

---

## 🎯 PRIMARY EXECUTION TASKS

### TASK 1: DAY 1 課程內容產出
**檔案輸出位置**: `course-content/day1/`

**需要產出的檔案:**
```
day1/
├── M0-environment-setup.md           # 環境準備 (30分鐘)
├── M1-core-concepts.md              # 核心概念 (60分鐘)
├── M2-claude-configuration.md       # .claude設定 (75分鐘)
├── M3-slash-commands.md             # Slash指令 (90分鐘)
├── M4-tdd-workflow.md               # TDD工作流 (90分鐘)
├── M8-memory-basics.md              # Memory基礎 (60分鐘)
├── lab1-claude-setup.md             # Lab 1: .claude目錄設定
├── lab2-api-commands.md             # Lab 2: 後端API指令系統
├── lab3-tdd-taskmanager.md          # Lab 3: TDD任務管理器
├── lab6-memory-monitor.md           # Lab 6: 記憶體監控工具
└── day1-instructor-guide.md         # 講師教學指南
```

**內容規格要求:**
- 每個模組包含：學習目標、技術重點、實作範例、檢核標準
- 每個 Lab 包含：前置準備、詳細步驟、預期結果、故障排除
- 所有程式碼範例必須可執行
- 包含時間分配與節奏控制建議

### TASK 2: DAY 2 課程內容產出
**檔案輸出位置**: `course-content/day2/`

**需要產出的檔案:**
```
day2/
├── M5-team-collaboration.md         # 團隊協作 (90分鐘)
├── M7-security-governance.md        # 安全治理 (90分鐘)
├── M8-memory-imports.md             # Memory匯入 (90分鐘)
├── M8-memory-cleanup.md             # Memory清理 (90分鐘)
├── M9-github-integration.md         # GitHub整合 (60分鐘)
├── lab4-git-worktree.md             # Lab 4: Git Worktree協作
├── lab7-file-import-strategy.md     # Lab 7: 檔案匯入策略
├── lab8-memory-automation.md        # Lab 8: 記憶體清理自動化
├── lab9-security-config.md          # Lab 9: 安全配置與Linter
├── lab10-github-automation.md       # Lab 10: GitHub Issue自動化
└── day2-instructor-guide.md         # 講師教學指南
```

### TASK 3: DAY 3 課程內容產出
**檔案輸出位置**: `course-content/day3/`

**需要產出的檔案:**
```
day3/
├── M6-cicd-integration.md           # CI/CD整合 (90分鐘)
├── M10-backend-development.md       # 後端開發 (90分鐘)
├── M10-frontend-integration.md      # 前端整合 (90分鐘)
├── fullstack-deployment.md         # 全端部署實戰 (90分鐘)
├── lab5-cicd-pipeline.md            # Lab 5: CI/CD Pipeline
├── lab11-spring-boot-api.md         # Lab 11: Spring Boot API
├── lab12-react-frontend.md          # Lab 12: React前端應用
└── day3-instructor-guide.md         # 講師教學指南
```

### TASK 4: 課程資源與範本產出
**檔案輸出位置**: `course-resources/`

**需要產出的檔案:**
```
course-resources/
├── templates/
│   ├── claude-setup-template/       # .claude目錄完整範本
│   ├── spring-boot-starter/         # Spring Boot專案範本
│   ├── react-frontend-starter/      # React前端專案範本
│   └── cicd-templates/              # CI/CD配置範本
├── checklists/
│   ├── environment-checklist.md     # 環境設定檢核表
│   ├── memory-management-checklist.md # 記憶體管理檢核表
│   ├── security-checklist.md        # 安全設定檢核表
│   └── deployment-checklist.md      # 部署檢核表
├── troubleshooting/
│   ├── common-issues.md             # 常見問題解決
│   ├── performance-tuning.md        # 效能調優指南
│   └── security-hardening.md        # 安全加固指南
└── assessment/
    ├── day1-assessment.md           # Day 1 評估表
    ├── day2-assessment.md           # Day 2 評估表
    ├── day3-assessment.md           # Day 3 評估表
    └── final-project-rubric.md      # 最終專案評分標準
```

---

## 🔧 技術規格與要求

### 程式碼標準
```yaml
要求:
  - 所有範例程式碼必須可直接執行
  - 遵循官方 Best Practice 標準
  - 包含完整的錯誤處理
  - 提供詳細的註解說明
  - 支援跨平台運行 (macOS, Linux, Windows WSL)

技術棧:
  Backend:
    - Spring Boot 3.2+
    - Java 17+
    - Spring Data JPA
    - H2/PostgreSQL
    - JUnit 5 + Testcontainers
  
  Frontend:
    - React 18
    - TypeScript 5+
    - Vite 5
    - React Query
    - Playwright (E2E測試)
  
  DevOps:
    - Docker & Docker Compose
    - GitHub Actions
    - Kubernetes (optional)
    - Prometheus + Grafana (monitoring)
```

### Claude Code 工具集成
```typescript
// 必須涵蓋的 16 個核心工具
const requiredTools = [
  'Read', 'Write', 'Edit', 'MultiEdit',  // 檔案操作
  'Glob', 'LS', 'Grep',                  // 檔案搜尋
  'Bash',                                // 命令執行
  'TodoRead', 'TodoWrite',               // 任務管理
  'WebFetch', 'WebSearch',               // 網路功能
  'NotebookRead', 'NotebookEdit',        // IDE整合
  'Agent',                               // 代理工具
  'exit_plan_mode'                       // 計畫模式
];
```

### 記憶體管理策略
```markdown
# 三層記憶體架構實作
1. 專案記憶體 (CLAUDE.md)
   - 團隊共享指令與規範
   - 專案特定配置與工作流程
   
2. 使用者記憶體 (~/.claude/CLAUDE.md)  
   - 個人偏好設定
   - 跨專案通用工具
   
3. 本機專案記憶體 (CLAUDE.local.md)
   - 個人專案特定設定
   - 本機開發環境配置
```

---

## 📚 內容結構範本

### 模組文件結構
```markdown
# 模組標題

## 🎯 學習目標
- 具體可測量的學習成果

## 📋 前置準備
- 必要的環境與知識準備

## 🔍 核心概念
- 理論背景與技術原理

## 💻 實作範例
- 可執行的程式碼範例
- 步驟化操作指南

## 🛠️ 實作練習
- 動手操作任務
- 預期結果驗證

## ✅ 檢核標準
- 學習成果驗證點
- 技能掌握度確認

## 🚨 常見問題
- 故障排除指南
- 最佳實踐建議

## 📖 延伸閱讀
- 相關官方文檔連結
- 進階學習資源
```

### Lab 操作手冊結構
```markdown
# Lab N: 實驗標題

## 🎯 實驗目標
- 明確的學習成果

## ⏱️ 預估時間
- XX 分鐘

## 📋 前置準備
### 環境需求
- 軟體版本要求
- 必要工具清單

### 知識準備  
- 相關概念回顧
- 參考資料連結

## 🔧 實驗步驟

### 步驟 1: [動作描述]
```bash
# 具體指令
command --options
```
**預期結果**: 詳細描述

### 步驟 2: [動作描述]
**操作**: 具體動作說明
**驗證**: 結果檢查方法

## ✅ 完成檢查
- [ ] 檢查點 1
- [ ] 檢查點 2
- [ ] 最終驗證

## 🚨 故障排除
### 問題 1: [常見錯誤]
**症狀**: 錯誤描述
**原因**: 問題分析  
**解決**: 具體步驟

## 🎉 實驗總結
- 學到的關鍵概念
- 實際應用場景
- 下一步學習建議
```

---

## 🚀 執行優先順序

1. **HIGH PRIORITY**: Day 1 課程內容 (新手基礎，最關鍵)
2. **HIGH PRIORITY**: 課程資源範本 (支撐所有課程)  
3. **MEDIUM PRIORITY**: Day 2 課程內容 (進階應用)
4. **MEDIUM PRIORITY**: Day 3 課程內容 (實戰專案)
5. **LOW PRIORITY**: 進階擴充內容

---

## ✅ 品質檢查清單

### 內容品質
- [ ] 所有程式碼範例可執行
- [ ] 每個步驟都有清楚說明
- [ ] 包含完整的錯誤處理
- [ ] 遵循官方 API 規範
- [ ] 符合企業級安全標準

### 教學品質  
- [ ] 學習目標明確可測
- [ ] 難度遞增合理
- [ ] 實作與理論平衡
- [ ] 提供充足的練習
- [ ] 故障排除完整

### 技術品質
- [ ] 整合 16 個核心工具
- [ ] 實作三層記憶體架構  
- [ ] 包含完整 CI/CD 流程
- [ ] 支援多種部署方式
- [ ] 遵循最佳實踐標準

---

## 🎯 SUCCESS CRITERIA

完成此執行計畫後，應達成：

1. **完整課程內容**: 3天24小時的詳細教學材料
2. **12個Lab手冊**: 可直接執行的實作指南
3. **豐富資源庫**: 範本、檢核表、故障排除指南
4. **評估體系**: 完整的學習成果驗證機制
5. **可擴充架構**: 支援後續課程發展需求

**開始執行吧！Let's build an amazing Claude Code curriculum! 🚀**
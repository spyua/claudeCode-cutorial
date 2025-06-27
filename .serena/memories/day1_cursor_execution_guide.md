# DAY 1 課程 Cursor Agent 執行指引

## 📋 已完成的記憶體內容

### 1. day1_course_structure
- 完整的 DAY 1 課程架構 (8小時)
- 6個模組的時程安排和學習目標
- 檢核標準和評估方式

### 2. m0_environment_setup_detailed  
- M0: 環境準備與IDE整合 (45分鐘)
- 詳細安裝步驟和IDE設定
- 故障排除和最佳實踐

### 3. m1_core_concepts_detailed
- M1: 核心概念與工具系統 (75分鐘)  
- 16個核心工具完整解析
- 互動模式和權限系統實作

### 4. m2_claude_configuration_and_lab1
- M2: CLAUDE.md專案配置 + Lab 1 (90分鐘)
- 三層記憶體架構實作
- 完整.claude目錄設定Lab

## 🚀 Cursor Agent 後續任務

### 待完成的 DAY 1 內容
```
還需要產出的模組:
├── M3: Slash指令系統 + Lab 2 (90分鐘)
├── M4: TDD工作流程 + Lab 3 (90分鐘) 
└── M5: Memory基礎管理 + Lab 4 (60分鐘)

還需要產出的Lab:
├── Lab 2: 後端API開發指令系統
├── Lab 3: TDD任務管理器實作
└── Lab 4: 記憶體監控工具
```

### 內容規格要求
每個模組應包含:
- 🎯 學習目標 (具體可測量)
- 📋 前置準備 (環境與知識需求)
- 🔍 核心概念 (理論背景)
- 💻 實作範例 (可執行程式碼)
- 🛠️ 實作練習 (動手操作)
- ✅ 檢核標準 (學習成果驗證)
- 🚨 常見問題 (故障排除)
- 📖 延伸學習 (參考資源)

每個Lab應包含:
- 🎯 實驗目標
- ⏱️ 預估時間
- 📋 前置準備
- 🔧 實驗步驟 (詳細步驟)
- ✅ 完成檢查
- 🚨 故障排除
- 🎉 實驗總結

### 技術標準要求
- 所有程式碼範例必須可執行
- 整合Claude Code 16個核心工具使用
- 遵循官方Best Practice標準
- 包含完整的錯誤處理和故障排除
- 支援跨平台運行 (macOS, Linux, Windows WSL)

## 📝 建議的 Cursor 執行步驟

1. **讀取已完成的記憶體內容**: 
   - 先讀取 day1_course_structure 了解整體架構
   - 讀取已完成的 M0, M1, M2 內容作為參考範例

2. **製作 M3 模組** (Slash指令系統):
   - 基於 build-with-claude 相關內容
   - 重點講解自定義指令開發
   - 包含 $ARGUMENTS 參數系統

3. **製作 Lab 2** (後端API開發指令系統):
   - 建立完整的API開發工作流程指令
   - 包含CRUD操作、測試、文檔生成指令

4. **製作 M4 模組** (TDD工作流程):
   - 整合Claude Code與測試驅動開發
   - 包含測試先行的開發模式

5. **製作 Lab 3** (TDD任務管理器):
   - 實作一個完整的TDD流程範例
   - 從測試撰寫到功能實作

6. **製作 M5 模組** (Memory基礎管理):
   - 深入記憶體管理策略
   - 效能監控與優化技巧

7. **製作 Lab 4** (記憶體監控工具):
   - 建立記憶體使用監控機制
   - 實作自動清理和優化工具

## 🎯 品質檢查清單

每個模組和Lab完成後應檢查:
- [ ] 內容結構完整 (包含所有必要章節)
- [ ] 程式碼範例可執行
- [ ] 時間分配合理 (符合課程設計)
- [ ] 學習目標明確可測
- [ ] 檢核標準具體可驗證
- [ ] 故障排除資訊完整
- [ ] 延伸學習資源相關

## 💾 存儲建議

建議將每個模組和Lab分別存儲為獨立的記憶體檔案:
- `m3_slash_commands_detailed`
- `lab2_api_development_commands`  
- `m4_tdd_workflow_detailed`
- `lab3_tdd_taskmanager`
- `m5_memory_management_detailed`
- `lab4_memory_monitoring_tool`

最後建立一個 `day1_complete_summary` 記憶體檔案，整合所有DAY 1內容的總結和使用指引。
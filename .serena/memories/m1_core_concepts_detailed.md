# M1: 核心概念與工具系統 (75分鐘)

## 🎯 學習目標
- 深度理解Claude Code的系統架構與工作原理
- 完全掌握16個核心工具的功能與使用時機
- 熟練運用各種互動模式與命令結構
- 建立正確的權限管理概念

## 📋 前置準備
- 已完成M0環境設定
- Claude Code可正常運作
- 已熟悉基本命令列操作

## 🔍 核心概念深度解析

### Claude Code系統架構
```
┌─────────────────────────────────────────┐
│             使用者介面層                 │
├─────────────────────────────────────────┤
│ Terminal CLI  │ IDE整合  │ SDK程式化     │
├─────────────────────────────────────────┤
│             核心工具層 (16個工具)        │
├─────────────────────────────────────────┤
│ 檔案操作 │ 程式分析 │ 網路功能 │ 專案管理 │
├─────────────────────────────────────────┤
│             權限與安全層                 │
├─────────────────────────────────────────┤
│ 工具權限控制 │ 安全模式 │ 稽核紀錄      │
├─────────────────────────────────────────┤
│             記憶體管理層                 │
├─────────────────────────────────────────┤
│ 專案記憶 │ 使用者記憶 │ 本機記憶       │
├─────────────────────────────────────────┤
│             API通訊層                   │
└─────────────────────────────────────────┘
│             Anthropic API               │
└─────────────────────────────────────────┘
```

### 16個核心工具完整解析

#### 1. 檔案操作工具群組 (6個)
```typescript
interface FileOperationTools {
  Read: {
    功能: "讀取檔案內容",
    參數: "file_path, offset?, limit?",
    使用時機: "查看檔案內容、理解程式碼結構"
  },
  
  Write: {
    功能: "寫入或覆蓋檔案",
    參數: "file_path, content",
    使用時機: "建立新檔案、完全重寫檔案"
  },
  
  Edit: {
    功能: "精確字串替換",
    參數: "file_path, old_string, new_string, replace_all?",
    使用時機: "小範圍程式碼修改、bug修復"
  },
  
  MultiEdit: {
    功能: "批次多重編輯",
    參數: "file_path, edits[]",
    使用時機: "同檔案多處修改、重構作業"
  },
  
  Glob: {
    功能: "檔案模式匹配",
    參數: "pattern, path?",
    使用時機: "批次檔案搜尋、專案結構探索"
  },
  
  LS: {
    功能: "目錄列表",
    參數: "path, ignore?",
    使用時機: "專案結構理解、檔案探索"
  }
}
```

#### 2. 程式分析工具群組 (1個)
```typescript
interface AnalysisTools {
  Grep: {
    功能: "內容搜尋與正規表達式匹配",
    參數: "pattern, include?, path?",
    使用時機: "程式碼搜尋、API使用追蹤、bug定位"
  }
}
```

#### 3. 執行環境工具群組 (1個)
```typescript
interface ExecutionTools {
  Bash: {
    功能: "執行shell命令",
    參數: "command, description?, timeout?",
    使用時機: "編譯、測試、部署、Git操作"
  }
}
```

#### 4. 專案管理工具群組 (2個)
```typescript
interface ProjectTools {
  TodoRead: {
    功能: "讀取任務清單",
    參數: "無",
    使用時機: "專案進度追蹤、任務狀態查詢"
  },
  
  TodoWrite: {
    功能: "管理任務清單",
    參數: "todos[]",
    使用時機: "任務規劃、進度管理、團隊協作"
  }
}
```

#### 5. 網路功能工具群組 (2個)
```typescript
interface NetworkTools {
  WebFetch: {
    功能: "抓取網頁內容並分析",
    參數: "url, prompt",
    使用時機: "API文檔查詢、技術資料蒐集"
  },
  
  WebSearch: {
    功能: "網路搜尋",
    參數: "query, allowed_domains?, blocked_domains?",
    使用時機: "技術問題解決、最新資訊查詢"
  }
}
```

#### 6. IDE整合工具群組 (2個)
```typescript
interface IDETools {
  NotebookRead: {
    功能: "讀取Jupyter筆記本",
    參數: "notebook_path, cell_id?",
    使用時機: "資料科學專案、研究筆記分析"
  },
  
  NotebookEdit: {
    功能: "編輯Jupyter筆記本",
    參數: "notebook_path, new_source, cell_type?, edit_mode?",
    使用時機: "資料分析結果更新、筆記本維護"
  }
}
```

#### 7. 工作流程工具群組 (2個)
```typescript
interface WorkflowTools {
  Agent: {
    功能: "啟動子代理執行任務",
    參數: "description, prompt",
    使用時機: "複雜任務分解、並行處理"
  },
  
  exit_plan_mode: {
    功能: "退出計畫模式",
    參數: "plan",
    使用時機: "完成任務規劃、開始執行階段"
  }
}
```

## 💻 互動模式深度實作

### 命令模式範例
```bash
# 1. 互動式REPL模式
claude

# 2. 一次性查詢模式
claude -p "explain the main function in src/app.js"

# 3. 繼續對話模式
claude --continue

# 4. 恢復特定會話
claude --resume session-abc123

# 5. 無頭模式 (自動化)
claude -p "run tests and fix any failures" --json
```

### 檔案參考語法實作
```bash
# @ 符號檔案參考
> 解釋 @src/utils/auth.js 的認證邏輯

# 範圍指定
> 檢查 @src/components/Header.tsx#L10-25 的props類型

# 多檔案參考
> 比較 @old/api.js 和 @new/api.ts 的差異

# GitHub檔案參考
> 分析 @github:owner/repo/blob/main/src/config.js 的設定
```

### 權限系統實作練習
```bash
# 檢查當前權限
/permissions

# 設定檔案編輯權限
> 我想要永遠允許Edit工具

# 設定特定命令權限
> 允許所有git相關的bash命令

# 企業模式權限
> 檢查我的團隊權限設定
```

## 🛠️ 綜合實作練習

### 練習1: 工具組合使用 (20分鐘)
```bash
# 步驟1: 探索專案結構
> 使用LS和Glob工具探索這個專案的結構

# 步驟2: 搜尋特定功能
> 使用Grep搜尋所有包含"authentication"的檔案

# 步驟3: 分析主要檔案
> 使用Read工具分析主要的配置檔案

# 步驟4: 建立修改計畫
> 使用TodoWrite建立一個改進認證系統的任務清單
```

### 練習2: 檔案操作流程 (15分鐘)
```bash
# 步驟1: 建立測試檔案
> 使用Write工具建立一個簡單的JavaScript模組

# 步驟2: 進行程式碼修改
> 使用Edit工具添加錯誤處理邏輯

# 步驟3: 批次修改
> 使用MultiEdit添加JSDoc註解和型別定義

# 步驟4: 驗證結果
> 使用Bash工具執行語法檢查
```

### 練習3: 網路資源整合 (10分鐘)
```bash
# 步驟1: 查詢API文檔
> 使用WebFetch獲取Express.js的最新文檔

# 步驟2: 搜尋解決方案
> 使用WebSearch查詢"Node.js最佳實踐2024"

# 步驟3: 整合到專案
> 根據查詢結果更新我們的專案配置
```

## ✅ 檢核標準

### 基礎能力檢核
- [ ] 能說出並演示16個核心工具的主要功能
- [ ] 理解每個工具的適用場景和使用時機
- [ ] 掌握@符號檔案參考的各種語法
- [ ] 能夠使用TodoWrite進行任務管理

### 進階能力檢核
- [ ] 能組合使用多個工具完成複雜任務
- [ ] 理解權限系統的設計理念和安全考量
- [ ] 掌握不同互動模式的使用場景
- [ ] 能夠進行基本的故障排除

### 實務能力檢核
- [ ] 能獨立完成專案結構分析任務
- [ ] 能使用工具鏈完成程式碼修改流程
- [ ] 能整合網路資源解決實際問題
- [ ] 建立了正確的工具使用習慣

## 🚨 常見問題與最佳實踐

### 工具選擇策略
```
決策樹:
需要讀取檔案? → Read
需要建立新檔案? → Write  
需要小幅修改? → Edit
需要大量修改? → MultiEdit
需要搜尋內容? → Grep
需要找檔案? → Glob
需要執行命令? → Bash
```

### 效能優化建議
1. **減少重複讀取**: 一次Read完整檔案，避免多次部分讀取
2. **批次操作**: 使用MultiEdit而非多次Edit
3. **精確搜尋**: Grep時使用include參數限制搜尋範圍
4. **權限預設**: 提前設定常用工具權限

### 安全使用原則
1. **最小權限**: 只給必要的工具權限
2. **命令檢查**: 執行Bash前確認命令安全性
3. **檔案備份**: 重要修改前先備份
4. **權限稽核**: 定期檢查權限設定

## 📖 延伸學習資源
- [Claude Code工具API參考](https://docs.anthropic.com/en/docs/claude-code/tools)
- [權限管理進階指南](https://docs.anthropic.com/en/docs/claude-code/security)
- [最佳實踐案例研究](https://docs.anthropic.com/en/docs/claude-code/best-practices)
- [故障排除完整指南](https://docs.anthropic.com/en/docs/claude-code/troubleshooting)
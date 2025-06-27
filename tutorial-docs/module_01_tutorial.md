# Module 01：Claude Code 基礎入門

## A. 學習目標
* 理解 Claude Code 基本概念與架構
* 完成安裝與初始化設定
* 熟悉互動模式與基本指令
* 執行專案分析與程式碼修改任務
* 建立良好使用習慣與問題排除能力

## B. 核心概念
### 1. Claude Code 簡介
- Anthropic AI 驅動的命令列開發工具，支援自然語言互動與程式設計輔助。

### 2. 系統架構與安全性
- 直接連接 Anthropic API，強調隱私與安全設計。

### 3. 互動模式與命令結構
- 提供互動式 REPL 與一次性命令，適用不同開發情境。

## C. 動手實驗
### 實驗 1：安裝與首次啟動
* **目標**: 成功安裝並啟動 Claude Code
* **前置準備**: Node.js 18+、Anthropic 帳號、網路
* **步驟**:
  1. `npm install -g @anthropic-ai/claude-code`
  2. `claude` 啟動
  3. 完成 OAuth 驗證
  4. 測試 `summarize this project`、`/help`
* **驗證**: `claude --version`、執行專案分析

### 實驗 2：專案分析與理解
* **目標**: 使用 Claude Code 進行專案結構分析
* **步驟**:
  1. 啟動 Claude Code
  2. `what does this project do?`
  3. `what technologies does this project use?`
  4. `explain the folder structure`
  5. `/init` 產生 CLAUDE.md
* **驗證**: 產生的 CLAUDE.md 是否正確

### 實驗 3：簡單程式碼修改
* **目標**: 完成第一個程式碼修改任務
* **步驟**:
  1. `add a hello world function to the main file`
  2. 檢視與批准建議
  3. 測試程式碼
  4. `commit my changes with a descriptive message`
  5. `show me the last 5 commits`
* **驗證**: 程式碼可執行、Git 記錄正確

## D. 常見問題與解決方案
- 安裝權限錯誤、WSL 問題、OAuth 驗證失敗、回應緩慢、修改不符預期

## E. 參考資源
- official-reference/getting-started/
- 官方 Discord

## F. 教學檢核清單
- 理論完整、步驟明確、實驗可重現、內容新手友善

---

> 詳細素材、工具、參考資源請見對應資料夾。

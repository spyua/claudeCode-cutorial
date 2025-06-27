# Module 01 教學規劃指引

## 📚 模組基本資訊
- **模組編號**: 01
- **模組標題**: Claude Code 基礎入門
- **目標學習者**: Claude Code 新手開發者
- **預計學習時間**: 2-3 小時
- **前置知識**: 基本命令列操作、基礎程式設計概念

## 🎯 學習目標
1. **理解 Claude Code 基本概念**：能夠解釋 Claude Code 是什麼，以及它如何協助開發工作
2. **掌握安裝和設定流程**：能夠獨立完成 Claude Code 的安裝、驗證和初始化設定
3. **熟悉基礎互動模式**：能夠啟動 Claude Code 並進行基本的對話互動
4. **執行第一個實用任務**：能夠使用 Claude Code 完成簡單的程式碼分析和修改任務
5. **建立良好使用習慣**：了解最佳實務和常見問題的預防方法

## 📖 教學內容規劃

### A. 核心概念 (理論部分)
#### 概念1: Claude Code 簡介
- **定義**: Claude Code 是 Anthropic 開發的 AI 驅動命令列工具，可直接在終端機中協助開發者進行程式設計工作
- **重要性**: 透過自然語言互動加速開發流程，無需離開熟悉的開發環境
- **使用場景**: 程式碼分析、bug 修復、功能開發、測試撰寫、Git 操作等
- **參考資料**: official-reference/getting-started/01.claude-Code-overview.md

#### 概念2: 系統架構與安全性
- **定義**: Claude Code 採用直接連接 Anthropic API 的架構，確保程式碼安全性
- **重要性**: 理解隱私保護機制，建立使用信心
- **使用場景**: 企業環境部署、敏感專案開發
- **參考資料**: official-reference/getting-started/01.claude-Code-overview.md (Security and privacy by design 章節)

#### 概念3: 互動模式與命令結構
- **定義**: Claude Code 提供互動式 REPL 介面和一次性命令模式
- **重要性**: 了解不同模式適用的工作情境
- **使用場景**: 長期開發會話 vs 快速查詢任務
- **參考資料**: official-reference/getting-started/03.quickstart.md

### B. 實用技巧 (操作部分)
#### 技巧1: 有效的提問技巧
- **適用情況**: 需要 Claude Code 理解複雜需求時
- **操作步驟**: 
  1. 使用具體描述而非模糊指令
  2. 提供足夠的上下文資訊
  3. 分步驟描述複雜任務
- **注意事項**: 避免過於簡短或含糊的指令
- **最佳實務**: "修復登入 bug，使用者輸入錯誤密碼後看到空白畫面" 而非 "修復 bug"

#### 技巧2: 專案初始化流程
- **適用情況**: 在新專案中首次使用 Claude Code
- **操作步驟**:
  1. 導航到專案目錄
  2. 執行 `claude` 啟動互動模式
  3. 執行 `/init` 產生 CLAUDE.md 專案指引
  4. 提交產生的檔案到版本控制
- **注意事項**: 確保在正確的專案根目錄執行
- **最佳實務**: 定期更新 CLAUDE.md 內容以反映專案變化

#### 技巧3: Git 整合操作
- **適用情況**: 需要進行版本控制相關操作時
- **操作步驟**:
  1. 使用自然語言描述 Git 操作需求
  2. 讓 Claude Code 執行相應的 Git 命令
  3. 確認變更內容後批准執行
- **注意事項**: 重要變更前先確認當前工作目錄狀態
- **最佳實務**: 使用描述性的提交訊息

## 🧪 實作實驗設計

### 實驗1: 安裝與首次啟動
- **實驗目標**: 成功安裝 Claude Code 並完成首次啟動
- **難度等級**: 初級
- **預計時間**: 30 分鐘
- **前置準備**: 
  - Node.js 18+ 已安裝
  - 擁有有效的 Anthropic 帳號
  - 網路連線正常
- **實驗步驟**:
  1. 執行 `npm install -g @anthropic-ai/claude-code` 安裝
  2. 在任意專案目錄執行 `claude` 啟動
  3. 完成 OAuth 驗證流程
  4. 測試基本指令：`summarize this project`
  5. 執行 `/help` 查看可用命令
- **預期結果**: 
  - 成功看到 Claude Code 歡迎畫面
  - 能夠正常執行基本查詢指令
  - 了解基本命令結構
- **驗證方法**: 
  - 檢查版本：`claude --version`
  - 成功執行一個簡單的專案分析任務
- **延伸挑戰**: 嘗試不同的驗證選項 (Console vs Claude App)

### 實驗2: 專案分析與理解
- **實驗目標**: 使用 Claude Code 深入理解一個既有專案
- **難度等級**: 初級
- **預計時間**: 45 分鐘
- **前置準備**: 準備一個簡單的程式專案 (或使用官方範例專案)
- **實驗步驟**:
  1. 在專案目錄啟動 Claude Code
  2. 執行專案概覽分析：`what does this project do?`
  3. 了解技術堆疊：`what technologies does this project use?`
  4. 分析專案結構：`explain the folder structure`
  5. 找出入口點：`where is the main entry point?`
  6. 執行 `/init` 產生專案指引
- **預期結果**:
  - 獲得專案的清晰概覽
  - 理解專案的技術架構
  - 產生有用的 CLAUDE.md 檔案
- **驗證方法**:
  - 檢查產生的 CLAUDE.md 是否包含準確的專案資訊
  - 能夠向他人清楚解釋專案用途和結構
- **延伸挑戰**: 比較 Claude Code 分析結果與專案實際文檔的差異

### 實驗3: 簡單程式碼修改
- **實驗目標**: 使用 Claude Code 完成第一個程式碼修改任務
- **難度等級**: 初級到中級
- **預計時間**: 60 分鐘
- **前置準備**: 
  - 有基本程式檔案的專案
  - Git 已初始化 (可選但建議)
- **實驗步驟**:
  1. 要求 Claude Code 添加簡單功能：`add a hello world function to the main file`
  2. 檢視建議的變更內容
  3. 批准或調整修改建議
  4. 測試修改後的程式碼
  5. 使用 Claude Code 提交變更：`commit my changes with a descriptive message`
  6. 檢查提交歷史：`show me the last 5 commits`
- **預期結果**:
  - 成功添加新功能到程式碼
  - 理解 Claude Code 的變更建議流程
  - 完成第一次透過 AI 輔助的程式碼提交
- **驗證方法**:
  - 確認程式碼能正常執行
  - 檢查 Git 提交記錄是否正確
  - 變更內容符合最初需求
- **延伸挑戰**: 
  - 嘗試更複雜的功能添加
  - 練習修復一個簡單的 bug

## ❓ 常見問題與解決方案

### Q1: 安裝時遇到權限錯誤
**問題描述**: 執行 npm install 時出現 EACCES 權限錯誤
**解決方案**: 
1. 絕對不要使用 `sudo npm install -g`
2. 配置 npm 全域目錄到使用者目錄
3. 或使用 nvm 管理 Node.js 版本
**預防方法**: 在安裝前正確配置 Node.js 和 npm 環境

### Q2: WSL 環境下無法正常運作
**問題描述**: 在 Windows WSL 中安裝或執行時出現錯誤
**解決方案**:
1. 確認使用 Linux 版本的 Node.js 而非 Windows 版本
2. 執行 `npm config set os linux` 
3. 使用 `--force --no-os-check` 參數安裝
**預防方法**: 使用 Linux 套件管理器或 nvm 安裝 Node.js

### Q3: 驗證流程無法完成
**問題描述**: OAuth 驗證失敗或無法連接到 Anthropic 服務
**解決方案**:
1. 檢查網路連線和防火牆設定
2. 確認在支援的國家/地區
3. 檢查 Anthropic 帳號狀態和計費設定
4. 嘗試不同的驗證選項
**預防方法**: 事先確認帳號狀態和網路環境

### Q4: Claude Code 回應緩慢或無回應
**問題描述**: 指令執行時間過長或沒有回應
**解決方案**:
1. 檢查網路連線穩定性
2. 嘗試重新啟動 Claude Code
3. 檢查是否有大量檔案需要分析
4. 使用更具體的指令減少處理範圍
**預防方法**: 保持網路連線穩定，避免在超大型專案中執行模糊查詢

### Q5: 程式碼修改建議不符合預期
**問題描述**: Claude Code 提供的程式碼修改不符合需求
**解決方案**:
1. 提供更詳細和具體的需求描述
2. 先讓 Claude Code 分析現有程式碼結構
3. 分步驟進行複雜修改
4. 使用範例或參考程式碼說明預期結果
**預防方法**: 學習有效的提問技巧，提供充分的上下文資訊

## 🔗 相關資源連結
- **官方文檔**: 
  - getting-started/01.claude-Code-overview.md - Claude Code 概覽
  - getting-started/02.set-up-claude-code.md - 安裝和設定指南
  - getting-started/03.quickstart.md - 快速開始教學
- **範例程式碼**: [claude-code-quickstart](https://github.com/anthropics/claude-code-quickstart)
- **延伸閱讀**: 
  - getting-started/04.memory-managment.md - 記憶體管理
  - getting-started/05.common-workflows.md - 常見工作流程
- **社群資源**: [Anthropic Discord](https://discord.gg/anthropic)

## 📋 教學檢核清單
### 內容完整性
- [x] 理論概念解釋清楚 - 涵蓋 Claude Code 基本概念、架構和互動模式
- [x] 實用技巧具體可操作 - 提供具體的操作步驟和最佳實務
- [x] 實驗設計循序漸進 - 從安裝到簡單程式碼修改，難度遞增
- [x] 常見問題覆蓋全面 - 包含安裝、設定、使用過程中的典型問題

### 教學品質
- [x] 語言簡潔易懂 - 使用新手友善的術語和解釋
- [x] 範例貼近實際應用 - 以實際開發情境為基礎
- [x] 難度適合新手 - 從基本操作開始，逐步深入
- [x] 與前後模組銜接良好 - 為後續進階模組建立基礎

## 🎬 後續執行計畫
此指引完成後，將由 Cursor 根據此規劃具體實作出：
- `tutorial-docs/module_01_tutorial.md` - 完整的教學文檔
- 相關的範例檔案和練習素材：
  - 示範專案結構
  - 練習用的程式碼範例
  - 實驗檢核清單
- 配套的檢核工具或腳本：
  - 安裝驗證腳本
  - 學習進度追蹤工具
  - 常見問題診斷工具
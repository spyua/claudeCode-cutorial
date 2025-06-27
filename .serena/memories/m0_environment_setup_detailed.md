# M0: 環境準備與IDE整合 (45分鐘)

## 🎯 學習目標
- 完成Claude Code的完整安裝與環境驗證
- 成功設定IDE整合(VS Code或JetBrains系列)
- 掌握基本快捷鍵與核心功能操作
- 建立穩定的開發環境基礎

## 📋 前置準備
### 系統需求檢查
```bash
# 檢查Node.js版本 (需要18+)
node --version

# 檢查npm版本
npm --version

# 檢查Git版本 (建議2.23+)
git --version

# 檢查可用記憶體 (建議4GB+)
free -h
```

### 必要軟體清單
- Node.js 18+ 
- npm (通常隨Node.js安裝)
- Git 2.23+
- VS Code 或 JetBrains IDE
- 穩定的網路連線

## 🔍 核心概念

### Claude Code架構
```
Claude Code 架構圖:
使用者 → 本地CLI → Anthropic API → Claude模型
       ↑
    IDE整合 (VS Code/JetBrains)
       ↑
    本地檔案系統 (.claude/配置)
```

### 支援的IDE環境
1. **Visual Studio Code系列**
   - VS Code (官方版本)
   - Cursor (AI增強版)
   - Windsurf (協作版本)

2. **JetBrains系列**
   - PyCharm (Python開發)
   - WebStorm (Web開發)
   - IntelliJ IDEA (Java開發)
   - GoLand (Go開發)

## 💻 實作步驟

### 步驟1: Claude Code安裝 (10分鐘)
```bash
# 全域安裝Claude Code
npm install -g @anthropic-ai/claude-code

# 驗證安裝
claude --version

# 首次啟動
claude
```

**預期結果**: 系統提示進行身份驗證

### 步驟2: 身份驗證設定 (10分鐘)
```bash
# 啟動Claude Code
claude

# 選擇認證方式:
# 1. Anthropic Console (預設)
# 2. Claude App (Pro/Max計畫)
# 3. 企業平台 (Bedrock/Vertex AI)
```

**驗證方法**:
```bash
# 測試基本功能
> hi, can you help me?
```

### 步驟3: VS Code整合設定 (15分鐘)
```bash
# 在VS Code中開啟終端
# 執行claude指令，擴充功能將自動安裝
claude

# 或者使用IDE指令
/ide
```

**VS Code功能驗證**:
- [ ] `Cmd+Esc` (Mac) 或 `Ctrl+Esc` (Windows/Linux) 快速啟動
- [ ] 差異檢視器整合
- [ ] 選擇內容自動共享
- [ ] `Cmd+Option+K` (Mac) 檔案參考快捷鍵
- [ ] 診斷錯誤自動分享

### 步驟4: JetBrains整合設定 (10分鐘)
1. 開啟JetBrains IDE
2. 前往Plugin Marketplace
3. 搜尋並安裝"Claude Code"插件
4. 重啟IDE
5. 測試快捷鍵功能

## 🛠️ 實作練習

### 練習1: 基本互動測試
```bash
# 啟動Claude Code
claude

# 測試檔案讀取
> read the README.md file

# 測試程式碼生成
> create a simple hello world function in JavaScript

# 測試檔案編輯
> add a comment to the function explaining what it does
```

### 練習2: IDE整合測試
1. 在IDE中開啟一個檔案
2. 使用快捷鍵啟動Claude Code
3. 測試選擇內容共享功能
4. 嘗試檔案參考功能

### 練習3: 權限系統測試
```bash
# 測試編輯權限
> modify this file to add a new function

# 觀察權限提示
# 選擇「Always allow」或「Allow once」

# 檢查權限設定
/permissions
```

## ✅ 檢核標準
- [ ] Claude Code成功安裝並可正常啟動
- [ ] 身份驗證完成，可以正常對話
- [ ] IDE整合設定完成，快捷鍵正常運作
- [ ] 能夠進行基本的檔案讀取與編輯操作
- [ ] 理解權限系統的基本概念
- [ ] 環境穩定，無明顯錯誤或延遲

## 🚨 常見問題排除

### 問題1: 安裝失敗
**症狀**: npm安裝時出現權限錯誤
**解決方案**:
```bash
# 使用sudo安裝 (Linux/Mac)
sudo npm install -g @anthropic-ai/claude-code

# 或設定npm權限
npm config set prefix ~/.npm-global
export PATH=~/.npm-global/bin:$PATH
```

### 問題2: IDE整合無法使用
**症狀**: 快捷鍵無反應
**解決方案**:
1. 確認IDE版本符合需求
2. 重新安裝插件
3. 檢查快捷鍵衝突
4. 重啟IDE

### 問題3: 網路連線問題
**症狀**: 認證失敗或API呼叫失敗
**解決方案**:
```bash
# 檢查網路連線
ping api.anthropic.com

# 檢查防火牆設定
# 確認443端口可用

# 使用代理設定
export HTTPS_PROXY=http://proxy.company.com:8080
```

## 📖 延伸學習
- [Claude Code官方文檔](https://docs.anthropic.com/en/docs/claude-code)
- [VS Code擴充功能使用指南](https://docs.anthropic.com/s/claude-code-vscode)
- [JetBrains插件使用指南](https://docs.anthropic.com/s/claude-code-jetbrains)
- [權限管理最佳實踐](https://docs.anthropic.com/en/docs/claude-code/security)
# M2: CLAUDE.md專案配置 + Lab 1 (90分鐘)

## 🎯 學習目標
- 深度理解CLAUDE.md的設計理念與架構
- 掌握三層記憶體管理系統的實作
- 建立專案專用的完整配置系統
- 透過Lab 1實作完整的.claude目錄結構

## 📋 前置準備
- 已完成M0和M1模組
- 理解Claude Code核心工具功能
- 準備一個練習專案目錄

## 🔍 核心概念深度解析

### CLAUDE.md設計理念
```markdown
CLAUDE.md = Claude Code的專案說明書
目的: 讓Claude快速理解專案脈絡，提供精準協助
原則: 簡潔、具體、可操作、可維護
```

### 三層記憶體架構詳解
```
記憶體層級架構:
┌─────────────────────────────────────┐
│  1. 全域使用者記憶體                  │
│     ~/.claude/CLAUDE.md              │
│     (個人偏好、通用工具、快捷指令)      │
├─────────────────────────────────────┤
│  2. 專案共享記憶體                   │
│     ./CLAUDE.md                     │
│     (團隊規範、專案指令、工作流程)      │
├─────────────────────────────────────┤
│  3. 本機專案記憶體                   │
│     ./CLAUDE.local.md               │
│     (個人專案設定、本機環境配置)        │
└─────────────────────────────────────┘
```

### 完整.claude目錄結構設計
```
.claude/
├── CLAUDE.md                    # 主要專案配置檔案
├── CLAUDE.local.md             # 本機專用配置 (git ignore)
├── settings.json               # 工具與權限設定
├── commands/                   # 自定義指令庫
│   ├── development.md          # 開發工作流程指令
│   ├── testing.md             # 測試相關指令
│   ├── deployment.md          # 部署相關指令
│   ├── git-workflows.md       # Git工作流程指令
│   └── troubleshooting.md     # 故障排除指令
├── templates/                  # 程式碼範本庫
│   ├── component-template.tsx  # React元件範本
│   ├── api-route-template.js   # API路由範本
│   ├── test-template.spec.js   # 測試檔案範本
│   └── docker-template.yml     # Docker配置範本
├── memory/                     # 專案記憶體檔案
│   ├── architecture.md        # 架構設計記錄
│   ├── decisions.md           # 技術決策記錄
│   └── conventions.md         # 程式碼規範記錄
├── scripts/                    # 自動化腳本
│   ├── setup.sh              # 環境設定腳本
│   ├── build.sh              # 建置腳本
│   └── deploy.sh             # 部署腳本
└── .gitignore                 # Claude專用忽略檔案
```

## 💻 模組內容實作 (45分鐘)

### CLAUDE.md最佳實踐結構
```markdown
# 專案名稱

## 🎯 專案概述
簡潔描述專案目的、核心功能、技術棧

## 🏗️ 架構設計
- 前端: React 18 + TypeScript + Vite
- 後端: Node.js + Express + MongoDB
- 部署: Docker + AWS ECS

## 🛠️ 常用指令
### 開發指令
- `npm run dev`: 啟動開發伺服器
- `npm run build`: 建置專案
- `npm run test`: 執行測試
- `npm run lint`: 程式碼檢查

### Git工作流程
- 使用GitFlow分支策略
- PR必須通過CI檢查
- 需要至少一位reviewer核可

## 📋 程式碼規範
- 使用ESLint + Prettier
- 遵循Airbnb JavaScript Style Guide
- 所有元件需要PropTypes或TypeScript型別
- API回應必須包含錯誤處理

## 🧪 測試策略
- 單元測試: Jest + Testing Library
- E2E測試: Cypress
- 測試覆蓋率需達80%以上

## 🚀 部署流程
- 開發分支 → Staging環境
- Main分支 → Production環境
- 使用藍綠部署策略

## ⚠️ 重要注意事項
- 敏感資料使用環境變數
- 所有API需要認證
- 遵循CORS安全設定
```

### settings.json配置範例
```json
{
  "permissions": {
    "defaultMode": "allowEdits",
    "allow": [
      "Edit",
      "Read", 
      "Write",
      "Bash(npm run:*)",
      "Bash(git:*)",
      "Bash(docker:*)"
    ],
    "deny": [
      "Bash(rm:*)",
      "Bash(sudo:*)"
    ]
  },
  "preferences": {
    "diffMode": "ide",
    "autoSave": true,
    "contextLimit": 50000
  },
  "project": {
    "name": "my-awesome-project",
    "type": "fullstack-web",
    "language": ["typescript", "javascript"],
    "framework": ["react", "express"]
  }
}
```

## 🧪 Lab 1: 完整.claude目錄設定實作 (45分鐘)

### 🎯 Lab目標
建立一個完整的.claude專案配置系統，包含所有必要的配置檔案、指令庫、範本庫和自動化腳本。

### ⏱️ 預估時間
45分鐘

### 📋 Lab前置準備
```bash
# 建立練習專案
mkdir claude-config-lab
cd claude-config-lab

# 初始化專案
npm init -y
git init

# 啟動Claude Code
claude
```

### 🔧 Lab實作步驟

#### 步驟1: 建立基礎目錄結構 (10分鐘)
```bash
# 在Claude Code中執行
> 請建立完整的.claude目錄結構，包含以下目錄和檔案：
> .claude/
> ├── CLAUDE.md
> ├── settings.json  
> ├── commands/
> ├── templates/
> ├── memory/
> ├── scripts/
> └── .gitignore

# 驗證結構
> 使用LS工具確認目錄結構正確建立
```

#### 步驟2: 建立CLAUDE.md主配置檔案 (15分鐘)
```markdown
# 使用Write工具建立CLAUDE.md
內容包含:
1. 專案概述
2. 技術棧說明
3. 常用開發指令
4. 程式碼規範
5. 測試策略
6. 部署流程
7. 安全注意事項
```

#### 步驟3: 建立自定義指令庫 (10分鐘)
```bash
# 建立開發工作流程指令
> 在.claude/commands/development.md中建立以下指令:
> - /dev:start - 啟動開發環境
> - /dev:build - 建置專案
> - /dev:test - 執行測試套件
> - /dev:lint - 程式碼檢查與修復

# 建立Git工作流程指令
> 在.claude/commands/git-workflows.md中建立:
> - /git:feature - 建立功能分支
> - /git:hotfix - 建立緊急修復分支  
> - /git:release - 準備發布版本
> - /git:cleanup - 清理本機分支
```

#### 步驟4: 建立程式碼範本庫 (10分鐘)
```typescript
// React元件範本
// .claude/templates/component-template.tsx
import React from 'react';

interface ${ComponentName}Props {
  // 定義props型別
}

export const ${ComponentName}: React.FC<${ComponentName}Props> = ({
  // 解構props
}) => {
  return (
    <div className="${component-name}">
      {/* 元件內容 */}
    </div>
  );
};

export default ${ComponentName};
```

```javascript
// API路由範本
// .claude/templates/api-route-template.js
const express = require('express');
const router = express.Router();

// GET /${routeName}
router.get('/', async (req, res) => {
  try {
    // 業務邏輯
    res.json({ success: true, data: [] });
  } catch (error) {
    res.status(500).json({ success: false, error: error.message });
  }
});

module.exports = router;
```

### ✅ Lab完成檢查
- [ ] .claude目錄結構完整建立
- [ ] CLAUDE.md包含所有必要章節
- [ ] settings.json配置適當的權限設定
- [ ] commands目錄包含至少5個自定義指令
- [ ] templates目錄包含至少3個程式碼範本
- [ ] 所有檔案都有適當的註解說明
- [ ] .gitignore正確忽略敏感檔案

### 🚨 Lab故障排除

#### 問題1: 目錄建立失敗
**症狀**: 權限不足或路徑錯誤
**解決**:
```bash
# 檢查當前目錄
> 使用LS確認目前位置

# 建立目錄
> 使用Bash工具: mkdir -p .claude/{commands,templates,memory,scripts}
```

#### 問題2: 檔案編碼問題
**症狀**: 中文字符顯示異常
**解決**:
```bash
# 檢查系統編碼
> echo $LANG

# 設定UTF-8編碼
> export LANG=en_US.UTF-8
```

## ✅ M2模組檢核標準
- [ ] 理解三層記憶體架構的設計理念
- [ ] 能獨立建立完整的.claude目錄結構
- [ ] 掌握CLAUDE.md的最佳實踐結構
- [ ] 了解settings.json的權限配置原則
- [ ] 能建立實用的自定義指令庫
- [ ] 能設計可重用的程式碼範本
- [ ] 完成Lab 1的所有實作要求

## 🚨 常見陷阱與最佳實踐

### 配置檔案常見錯誤
1. **過度詳細**: CLAUDE.md不是documentation，要保持簡潔
2. **缺乏維護**: 配置檔案需要隨專案演進更新
3. **權限過寬**: settings.json不應該給予過多權限
4. **忽略本機設定**: 忘記建立CLAUDE.local.md

### 最佳實踐建議
1. **版本控制**: 將CLAUDE.md納入Git管理
2. **團隊同步**: 定期檢查團隊成員的配置一致性
3. **分層設定**: 全域、專案、本機設定要有明確分工
4. **安全優先**: 敏感資訊絕不寫入配置檔案

## 📖 延伸學習
- [CLAUDE.md進階配置指南](https://docs.anthropic.com/en/docs/claude-code/memory)
- [權限管理最佳實踐](https://docs.anthropic.com/en/docs/claude-code/security)
- [團隊協作配置策略](https://docs.anthropic.com/en/docs/claude-code/collaboration)
- [自定義指令開發指南](https://docs.anthropic.com/en/docs/claude-code/slash-commands)
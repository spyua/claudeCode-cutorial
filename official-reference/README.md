# Official Reference

## 目錄內容

### 核心文件
- `claude-code-official-best-practice-doc.md` - Claude Code 官方最佳實踐指南 (29KB, 395行)

### 子目錄

#### `getting-started/` - 新手入門指南
- `01.claude-Code-overview.md` - Claude Code 概覽 (3.2KB, 91行)
- `02.set-up-claude-code.md` - 設定 Claude Code (6.1KB, 177行)
- `03.quickstart.md` - 快速開始指南 (5.8KB, 243行)
- `04.memory-managment.md` - 記憶體管理 (4.3KB, 89行)
- `05.common-workflows.md` - 常見工作流程 (20KB, 775行)

#### `build-with-claude/` - 與 Claude 一起建構
- `01.add-claude-code-to-your-IDE.md` - 將 Claude Code 加入您的 IDE (3.9KB, 110行)
- `02.model-context-protocol.md` - 模型上下文協議 (13KB, 399行)
- `03.claude-code-github-actions.md` - Claude Code GitHub Actions (22KB, 538行)
- `04.claude-code.sdk.md` - Claude Code SDK (21KB, 570行)
- `05.troubleshooting.md` - 故障排除 (6.5KB, 208行)

#### `reference/` - 參考文件
- `claude-code-settings.md` - Claude Code 設定 (15KB, 170行)
- `slash-commands.md` - 斜線命令 (4.1KB, 96行)
- `Interactive-mode.md` - 互動模式 (4.1KB, 96行)
- `cli-reference.md` - CLI 參考 (6.7KB, 57行)

## 快速開始

### 閱讀順序
1. **新手**: 從 `getting-started/` 目錄開始
   - 先讀 `01.claude-Code-overview.md` 了解基本概念
   - 接著 `02.set-up-claude-code.md` 進行環境設定
   - 然後 `03.quickstart.md` 進行實作練習
   - 最後 `04.memory-managment.md` 和 `05.common-workflows.md` 深入學習

2. **進階用戶**: 直接閱讀核心文件
   - `claude-code-official-best-practice-doc.md` - 官方最佳實踐

3. **開發者**: 查看 `build-with-claude/` 和 `reference/` 目錄
   - 整合到 IDE 和 CI/CD 流程
   - 使用 SDK 和 API

### 重點章節
- **環境設定**: CLAUDE.md 檔案、權限管理、工具整合
- **工作流程**: 探索→規劃→編碼→提交、TDD、視覺迭代
- **安全治理**: 權限控制、安全模式、團隊協作
- **記憶體管理**: 上下文管理、清理策略、效能優化
- **團隊協作**: GitHub 整合、版本控制、CI/CD

## 搜尋命令

```bash
# 搜尋權限相關
grep -i "permission" claude-code-official-best-practice-doc.md

# 搜尋工作流程
grep -i "workflow" claude-code-official-best-practice-doc.md

# 搜尋安全相關
grep -i "security\|safety" claude-code-official-best-practice-doc.md

# 搜尋記憶體相關
grep -i "memory" getting-started/04.memory-managment.md

# 搜尋設定相關
grep -i "setting\|config" reference/claude-code-settings.md
```

## 相關連結
- 官方網站: https://claude.ai/code
- 技術文件: https://docs.anthropic.com/claude/docs/claude-code
- GitHub 儲存庫: https://github.com/anthropics/anthropic-cookbook

## 更新記錄
- 2025-01-XX: 初始版本
- 2025-01-XX: 新增完整目錄結構和詳細說明

# 更新的建議指令清單

## Claude Code 自定義指令

### 📚 教學模組開發指令
```bash
# 產生教學模組規劃指引 (新增)
/generate_module_guide [模組編號]     # 產生完整的教學模組規劃指引

# 原有的教學模組指令
/new_module [模組標題]              # 建立新的教學模組
/add_experiment [檔案路徑]          # 新增實驗到現有模組  
/review_module [檔案路徑]           # 從新手角度檢視模組
```

### 使用範例
```bash
# 步驟1: Claude Code 產生規劃指引
/generate_module_guide M01

# 步驟2: Cursor 根據指引實作教學文檔
# (此步驟由 Cursor 執行，產出到 tutorial-docs/ 資料夾)

# 步驟3: 檢視和改進教學內容
/review_module tutorial-docs/module_M01_tutorial.md
```

## Git 相關指令
```bash
# 基本版本控制
git status
git add .
git commit -m "描述性的中文提交訊息"
git push origin main
git log --oneline -10

# 分支操作
git branch
git checkout -b new-feature
git merge feature-branch
```

## 文檔管理指令
```bash
# 檔案操作
ls -la                           # 列出所有檔案(包含隱藏)
find . -name "*.md"              # 尋找所有Markdown檔案
mkdir -p tutorial-docs           # 建立教學文檔資料夾
mkdir -p docs/new-module         # 建立新的模組資料夾

# 文檔預覽
code filename.md                 # 用VS Code開啟檔案
```

## 協作工作流程指令
```bash
# 工作紀錄管理
touch WORK_LOG.md               # 建立工作紀錄檔案
echo "[時間] [執行者] [狀態] [描述]" >> WORK_LOG.md

# Serena Memory 操作
# (透過 Claude Code 的內建工具執行)
# - 讀取記憶體: read_memory
# - 寫入記憶體: write_memory  
# - 列出記憶體: list_memories
```

## 系統工具指令
```bash
# Linux 基本指令
pwd                             # 顯示當前路徑
cat filename                    # 顯示檔案內容
grep "搜尋內容" *.md             # 在Markdown檔案中搜尋
find . -type f -name "*.md"     # 尋找特定類型檔案

# 檔案結構檢查
tree                           # 顯示目錄樹狀結構
ls -la tutorial-docs/          # 檢查教學文檔目錄
```

## NPM/建置相關 (未來可能用到)
```bash
# 專案建置
npm install
npm run build  
npm run dev
npm run lint                   # 程式碼檢查
npm run test                   # 執行測試
```

## 教學品質檢核指令
```bash
# 文檔品質檢查
wc -l tutorial-docs/*.md       # 檢查文檔行數
grep -c "##" tutorial-docs/*.md # 檢查章節數量

# 連結有效性檢查 (如有相關工具)
# markdown-link-check tutorial-docs/*.md
```

## 模組編號參考
```bash
# 基礎模組
/generate_module_guide M01     # Claude Code 概述與安裝
/generate_module_guide M02     # 基本使用與 .claude 設定  
/generate_module_guide M03     # Slash 指令系統
/generate_module_guide M04     # TDD 開發流程
/generate_module_guide M05     # 團隊協作功能

# 進階模組  
/generate_module_guide M06     # CI/CD 整合
/generate_module_guide M07     # 安全性與權限管理
/generate_module_guide M08     # Memory 管理系統
/generate_module_guide M09     # GitHub Issue 整合
/generate_module_guide M10     # 全端專案實戰
```

## 協作流程快速參考
```bash
# 1. Claude Code 階段
/generate_module_guide [編號]   # 產生規劃指引
# 檢查 Serena Memory 中的 module_[編號]_guide.md

# 2. Cursor 階段 (由 Cursor 執行)
# - 讀取指引
# - 實作教學文檔到 tutorial-docs/
# - 更新工作紀錄

# 3. 品質檢核階段
/review_module [教學文檔路徑]    # 檢視教學品質
git add . && git commit -m "新增模組[編號]教學文檔"
```

## 注意事項
1. **協作順序**: 務必先執行 `/generate_module_guide` 再讓 Cursor 實作
2. **檔案路徑**: 確保 `tutorial-docs/` 資料夾存在
3. **版本控制**: 每完成一個模組都要進行 git commit
4. **品質檢查**: 使用 `/review_module` 確保教學品質
5. **記憶體管理**: 定期檢查 Serena Memory 的使用狀況
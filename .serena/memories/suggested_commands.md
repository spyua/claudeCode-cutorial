# 建議使用的指令

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
ls -la                    # 列出所有檔案(包含隱藏)
find . -name "*.md"       # 尋找所有Markdown檔案
mkdir -p docs/new-module  # 建立新的模組資料夾

# 文檔預覽
code filename.md          # 用VS Code開啟檔案
```

## Claude Code 自定義指令
```bash
# 教學模組相關
/new_module [模組標題]              # 建立新的教學模組
/add_experiment [檔案路徑]          # 新增實驗到現有模組
/review_module [檔案路徑]           # 從新手角度檢視模組
```

## 系統工具指令
```bash
# Linux 基本指令
pwd                       # 顯示當前路徑
cat filename              # 顯示檔案內容
grep "搜尋內容" *.md       # 在Markdown檔案中搜尋
find . -type f -name      # 檔案尋找
```

## NPM/建置相關 (如有需要)
```bash
# 專案建置 (未來可能用到)
npm install
npm run build
npm run dev
```

## 注意事項
- 所有操作都在專案根目錄執行
- 使用中文進行提交訊息
- 遵循既有的檔案命名慣例
- 建立新檔案前先確認目錄結構
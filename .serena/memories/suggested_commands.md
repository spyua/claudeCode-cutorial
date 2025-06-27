# 建議的系統指令

## 檔案操作
```bash
# 檢視專案結構
ls -la
tree -a -I '.git'

# 搜尋特定內容
grep -r "Claude Code" .
find . -name "*.md" -type f

# 檔案統計
wc -l *.md
du -sh */
```

## Git 操作
```bash
# 基本 Git 指令
git status
git add .
git commit -m "message"
git push origin main

# 分支操作
git branch -a
git checkout -b new-feature
git merge feature-branch
```

## 文檔處理
```bash
# Markdown 檢查
markdownlint *.md

# 內容統計
find . -name "*.md" -exec wc -l {} + | sort -n

# 大檔案檢查
find . -size +100k -type f
```

## 課程開發相關
```bash
# 產生課程目錄
mkdir -p course-content/{day1,day2,day3}
mkdir -p course-resources/{templates,checklists,troubleshooting,assessment}

# 備份重要檔案
cp COMPREHENSIVE_CURRICULUM_PLAN.md backups/
cp SERENA_EXECUTION_PLAN.md backups/
```

## 系統監控
```bash
# 磁碟空間檢查
df -h
du -sh . 

# 記憶體使用
free -h
top -n 1 -b | head -20
```
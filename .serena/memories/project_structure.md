# 專案結構說明

## 根目錄結構
```
claudeCode-cutorial/
├── .claude/                    ← Claude Code配置目錄
│   ├── settings.json           ← 專案設定檔
│   ├── settings.local.json     ← 本地設定檔  
│   └── command/                ← 自定義指令目錄
│       ├── review_module.md    ← 模組檢視指令
│       ├── add_experiment.md   ← 新增實驗指令
│       └── new_module.md       ← 新建模組指令
├── _instructor-materials/      ← 教學素材目錄
│   ├── README.md              ← (空檔案)
│   └── teaching-materials-summary.md ← 完整教學素材總結
├── official-reference/         ← 官方參考文檔
│   ├── README.md              ← 參考文檔說明
│   ├── reference/             ← 參考文檔
│   ├── getting-started/       ← 入門文檔
│   └── build-with-claude/     ← 進階整合文檔
├── .git/                      ← Git版本控制
├── .serena/                   ← Serena記憶體目錄
└── README.md                  ← 專案說明檔
```

## 重要目錄說明

### .claude/ 目錄
- **settings.json**: 專案核心配置，包含模型、語言、權限設定
- **command/**: 自定義指令集，提供教學文檔的快速操作範本

### _instructor-materials/ 目錄  
- 包含完整的三天制課程規劃
- 教學素材、實作範例、檢核標準
- 講師教學指南與常見問題解答

### official-reference/ 目錄
- Claude Code官方文檔的本地副本
- 涵蓋入門、參考、進階整合等內容
- 作為課程開發的權威參考資料

## 擴展規劃
未來可能新增的目錄:
- `docs/`: 課程模組文檔
- `examples/`: 實作範例程式碼  
- `templates/`: 專案範本
- `assets/`: 教學圖片與資源
# 技術棧

## 主要技術
- **文檔格式**: Markdown (.md檔案)
- **版本控制**: Git
- **語言設定**: 繁體中文 (zh-TW)
- **專案類型**: 文檔教學專案

## 工具配置
- **編輯器**: VS Code (command: "code", args: ["-r", "-g"])
- **Claude Code**: 使用 Sonnet 4 模型
- **權限管理**: 細緻的檔案存取控制

## 專案結構
```
claudeCode-cutorial/
├── .claude/                 ← Claude Code配置
│   ├── settings.json        ← 專案設定
│   └── command/             ← 自定義指令
├── _instructor-materials/   ← 教學素材
├── official-reference/      ← 官方參考文檔
└── README.md               ← 專案說明
```

## 課程涵蓋技術
- **後端**: Spring Boot 3
- **前端**: React + Vite  
- **基礎設施**: Docker & Kubernetes
- **CI/CD**: GitHub Actions
- **測試**: TDD開發流程
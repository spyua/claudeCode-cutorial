# M3: Slash指令系統 + Lab 2 (90分鐘)

## 🎯 學習目標
- 深度理解Slash指令系統的設計理念與架構
- 掌握$ARGUMENTS參數系統與指令鏈結技術
- 建立企業級API開發指令庫
- 透過Lab 2實作完整的後端API開發工作流程

## 📋 前置準備
- 已完成M0、M1、M2模組
- 理解.claude目錄結構與配置
- 熟悉Claude Code核心工具操作
- 準備Node.js開發環境

## 🔍 核心概念深度解析

### Slash指令系統架構
```
Slash指令執行流程:
使用者輸入 → 指令解析 → 參數替換 → Claude執行 → 結果回傳

/command:action arg1 arg2
    ↓
.claude/commands/command.md
    ↓
$ARGUMENTS替換為 "action arg1 arg2"
    ↓
Claude執行指令內容
    ↓
輸出結果與狀態
```

### 指令分類與設計原則
```typescript
interface SlashCommandTypes {
  工作流程指令: {
    目的: "自動化開發流程",
    範例: "/dev:start, /build:prod, /deploy:staging",
    特點: "包含多個步驟，需要錯誤處理"
  },
  
  程式碼生成指令: {
    目的: "快速產生程式碼骨架",
    範例: "/create:component, /gen:api, /make:test",
    特點: "使用範本替換，支援參數化"
  },
  
  專案管理指令: {
    目的: "管理專案狀態與任務",
    範例: "/task:create, /status:check, /review:code",
    特點: "整合外部工具，提供報告"
  },
  
  故障排除指令: {
    目的: "診斷與修復問題",
    範例: "/fix:lint, /debug:test, /health:check",
    特點: "智慧診斷，自動修復"
  }
}
```

### $ARGUMENTS參數系統詳解
```markdown
# 參數系統語法
$ARGUMENTS - 完整參數字串
$ARG1, $ARG2, $ARG3 - 個別參數 (以空格分隔)
${COMPONENT_NAME} - 具名參數 (需要額外解析)
${file:path/to/file} - 檔案內容參數
${date:YYYY-MM-DD} - 動態值參數

# 進階參數處理
${ARGUMENTS:default=value} - 預設值
${ARG1:upper} - 大寫轉換
${ARG2:kebab} - kebab-case轉換
${ARG3:camel} - camelCase轉換
```

## 💻 Slash指令開發實作 (45分鐘)

### 基礎指令結構範本
```markdown
# .claude/commands/template.md

請執行 $ARGUMENTS 相關的操作。

## 執行步驟:
1. 驗證參數有效性
2. 檢查前置條件  
3. 執行主要邏輯
4. 驗證結果
5. 提供狀態報告

## 錯誤處理:
- 參數無效: 提供使用說明
- 前置條件不滿足: 指導如何修復
- 執行失敗: 分析原因並建議解決方案

## 成功標準:
- 所有步驟順利完成
- 結果符合預期
- 無遺留問題
```

### 實務指令範例集

#### 1. API開發工作流程指令
```markdown
# .claude/commands/api.md

請為 $ARGUMENTS API端點建立完整的開發實作。

## 開發流程:

### 1. API設計階段 (10分鐘)
- 分析需求: $ARG1 (端點名稱)
- 設計RESTful API規格
- 定義請求/回應格式
- 規劃錯誤處理策略

### 2. 程式碼實作階段 (15分鐘)
```javascript
// 建立Express路由檔案
const express = require('express');
const router = express.Router();
const { validate, authenticate } = require('../middleware');

// ${ARG1} API implementation
router.get('/', authenticate, async (req, res) => {
  try {
    // 業務邏輯實作
    const result = await ${ARG1}Service.getAll(req.query);
    res.json({ success: true, data: result });
  } catch (error) {
    res.status(500).json({ 
      success: false, 
      error: error.message 
    });
  }
});

router.post('/', authenticate, validate(${ARG1}Schema), async (req, res) => {
  try {
    const result = await ${ARG1}Service.create(req.body);
    res.status(201).json({ success: true, data: result });
  } catch (error) {
    res.status(400).json({ 
      success: false, 
      error: error.message 
    });
  }
});

module.exports = router;
```

### 3. 測試實作階段 (10分鐘)
- 建立單元測試
- 建立整合測試  
- 執行測試驗證
- 確保測試覆蓋率

### 4. 文檔生成階段 (5分鐘)
- 自動生成API文檔
- 建立使用範例
- 更新Swagger規格

## 品質檢查:
- [ ] API符合RESTful設計原則
- [ ] 包含完整的錯誤處理
- [ ] 測試覆蓋率達80%以上
- [ ] API文檔清楚完整
- [ ] 通過security檢查

使用方式: `/api:create UserAuth` 或 `/api:update ProductCatalog`
```

#### 2. 程式碼生成指令
```markdown
# .claude/commands/generate.md

請根據 $ARGUMENTS 規格生成對應的程式碼結構。

## 生成類型判斷:
- component: React元件
- service: 業務邏輯服務  
- model: 資料模型
- test: 測試檔案
- config: 配置檔案

## React元件生成 (當$ARG1 = component):
```typescript
// src/components/${ARG2}/${ARG2}.tsx
import React from 'react';
import styles from './${ARG2}.module.css';

interface ${ARG2}Props {
  // TODO: 定義props型別
}

export const ${ARG2}: React.FC<${ARG2}Props> = ({
  // TODO: 解構props
}) => {
  return (
    <div className={styles.${ARG2:kebab}}>
      <h2>${ARG2} Component</h2>
      {/* TODO: 實作元件邏輯 */}
    </div>
  );
};

export default ${ARG2};
```

```css
/* src/components/${ARG2}/${ARG2}.module.css */
.${ARG2:kebab} {
  /* TODO: 樣式定義 */
}
```

## 業務服務生成 (當$ARG1 = service):
```typescript
// src/services/${ARG2}Service.ts
export class ${ARG2}Service {
  
  async getAll(filters?: any): Promise<${ARG2}[]> {
    // TODO: 實作查詢邏輯
    throw new Error('Method not implemented');
  }
  
  async getById(id: string): Promise<${ARG2} | null> {
    // TODO: 實作單筆查詢
    throw new Error('Method not implemented');
  }
  
  async create(data: Create${ARG2}Request): Promise<${ARG2}> {
    // TODO: 實作建立邏輯
    throw new Error('Method not implemented');
  }
  
  async update(id: string, data: Update${ARG2}Request): Promise<${ARG2}> {
    // TODO: 實作更新邏輯  
    throw new Error('Method not implemented');
  }
  
  async delete(id: string): Promise<boolean> {
    // TODO: 實作刪除邏輯
    throw new Error('Method not implemented');
  }
}

export const ${ARG2:camel}Service = new ${ARG2}Service();
```

## 執行後檢查:
- [ ] 檔案結構正確建立
- [ ] 程式碼符合專案規範
- [ ] TypeScript型別定義完整
- [ ] 包含適當的TODO標記

使用方式: `/generate:component UserProfile` 或 `/generate:service ProductManager`
```

#### 3. 測試與品質保證指令
```markdown
# .claude/commands/quality.md

請對 $ARGUMENTS 進行全面的品質檢查與測試。

## 品質檢查流程:

### 1. 靜態程式碼分析 (5分鐘)
```bash
# ESLint檢查
npm run lint

# TypeScript型別檢查
npm run type-check

# 程式碼格式檢查
npm run format:check
```

### 2. 測試執行 (15分鐘)
```bash
# 單元測試
npm run test:unit

# 整合測試
npm run test:integration

# E2E測試
npm run test:e2e

# 測試覆蓋率報告
npm run test:coverage
```

### 3. 安全性檢查 (5分鐘)
```bash
# 依賴漏洞掃描
npm audit

# 安全性規則檢查
npm run security:check
```

### 4. 效能分析 (5分鐘)
```bash
# Bundle大小分析
npm run build:analyze

# 記憶體使用分析
npm run memory:profile
```

## 自動修復功能:
如果發現問題，自動執行修復:
- ESLint錯誤: `npm run lint:fix`
- 格式問題: `npm run format`
- 依賴更新: `npm update`
- 型別錯誤: 提供修復建議

## 報告生成:
生成詳細的品質報告，包含:
- 測試結果總結
- 程式碼覆蓋率
- 安全性檢查結果
- 效能指標
- 改進建議

使用方式: `/quality:check all` 或 `/quality:fix lint`
```

## 🧪 Lab 2: 後端API開發指令系統實作 (45分鐘)

### 🎯 Lab目標
建立一套完整的後端API開發指令系統，包含API設計、實作、測試、文檔生成的自動化工作流程。

### ⏱️ 預估時間
45分鐘

### 📋 Lab前置準備
```bash
# 建立練習專案
mkdir api-development-lab
cd api-development-lab

# 初始化Node.js專案
npm init -y

# 安裝必要依賴
npm install express cors helmet morgan dotenv
npm install -D jest supertest nodemon eslint

# 建立基礎目錄結構
mkdir -p src/{routes,controllers,services,models,middleware,tests}

# 啟動Claude Code
claude
```

### 🔧 Lab實作步驟

#### 步驟1: 建立API開發指令庫 (15分鐘)
```bash
# 在Claude Code中執行
> 請在.claude/commands/目錄建立以下API開發指令檔案:

# 1. api-crud.md - CRUD API生成指令
> 建立 /api:crud 指令，能夠生成完整的CRUD API端點

# 2. api-test.md - API測試指令  
> 建立 /api:test 指令，自動生成API測試檔案

# 3. api-docs.md - API文檔指令
> 建立 /api:docs 指令，生成Swagger API文檔

# 4. api-deploy.md - API部署指令
> 建立 /api:deploy 指令，處理API部署流程
```

#### 步驟2: 實作CRUD API生成指令 (15分鐘)
```markdown
# .claude/commands/api-crud.md

請為 $ARGUMENTS 實體建立完整的CRUD API。

## 1. 建立資料模型 ($ARG1)
建立 src/models/${ARG1}.js:
```javascript
const mongoose = require('mongoose');

const ${ARG1}Schema = new mongoose.Schema({
  // TODO: 定義欄位結構
  name: {
    type: String,
    required: true,
    trim: true
  },
  description: {
    type: String,
    default: ''
  },
  status: {
    type: String,
    enum: ['active', 'inactive'],
    default: 'active'
  },
  createdAt: {
    type: Date,
    default: Date.now
  },
  updatedAt: {
    type: Date,
    default: Date.now
  }
});

${ARG1}Schema.pre('save', function(next) {
  this.updatedAt = Date.now();
  next();
});

module.exports = mongoose.model('${ARG1}', ${ARG1}Schema);
```

## 2. 建立業務服務
建立 src/services/${ARG1}Service.js:
```javascript
const ${ARG1} = require('../models/${ARG1}');

class ${ARG1}Service {
  async getAll(filters = {}, options = {}) {
    const { page = 1, limit = 10, sort = '-createdAt' } = options;
    const skip = (page - 1) * limit;
    
    const query = ${ARG1}.find(filters);
    const total = await ${ARG1}.countDocuments(filters);
    const items = await query
      .sort(sort)
      .skip(skip)
      .limit(parseInt(limit));
    
    return {
      items,
      pagination: {
        page: parseInt(page),
        limit: parseInt(limit),
        total,
        pages: Math.ceil(total / limit)
      }
    };
  }
  
  async getById(id) {
    return await ${ARG1}.findById(id);
  }
  
  async create(data) {
    const item = new ${ARG1}(data);
    return await item.save();
  }
  
  async update(id, data) {
    return await ${ARG1}.findByIdAndUpdate(
      id, 
      { ...data, updatedAt: Date.now() }, 
      { new: true, runValidators: true }
    );
  }
  
  async delete(id) {
    return await ${ARG1}.findByIdAndDelete(id);
  }
}

module.exports = new ${ARG1}Service();
```

## 3. 建立控制器
建立 src/controllers/${ARG1}Controller.js:
```javascript
const ${ARG1}Service = require('../services/${ARG1}Service');

const ${ARG1}Controller = {
  // GET /${ARG1:kebab}
  async getAll(req, res) {
    try {
      const { page, limit, sort, ...filters } = req.query;
      const result = await ${ARG1}Service.getAll(filters, { page, limit, sort });
      res.json({ success: true, ...result });
    } catch (error) {
      res.status(500).json({ success: false, error: error.message });
    }
  },
  
  // GET /${ARG1:kebab}/:id
  async getById(req, res) {
    try {
      const item = await ${ARG1}Service.getById(req.params.id);
      if (!item) {
        return res.status(404).json({ success: false, error: '${ARG1} not found' });
      }
      res.json({ success: true, data: item });
    } catch (error) {
      res.status(500).json({ success: false, error: error.message });
    }
  },
  
  // POST /${ARG1:kebab}
  async create(req, res) {
    try {
      const item = await ${ARG1}Service.create(req.body);
      res.status(201).json({ success: true, data: item });
    } catch (error) {
      if (error.name === 'ValidationError') {
        res.status(400).json({ success: false, error: error.message });
      } else {
        res.status(500).json({ success: false, error: error.message });
      }
    }
  },
  
  // PUT /${ARG1:kebab}/:id
  async update(req, res) {
    try {
      const item = await ${ARG1}Service.update(req.params.id, req.body);
      if (!item) {
        return res.status(404).json({ success: false, error: '${ARG1} not found' });
      }
      res.json({ success: true, data: item });
    } catch (error) {
      res.status(500).json({ success: false, error: error.message });
    }
  },
  
  // DELETE /${ARG1:kebab}/:id
  async delete(req, res) {
    try {
      const item = await ${ARG1}Service.delete(req.params.id);
      if (!item) {
        return res.status(404).json({ success: false, error: '${ARG1} not found' });
      }
      res.json({ success: true, message: '${ARG1} deleted successfully' });
    } catch (error) {
      res.status(500).json({ success: false, error: error.message });
    }
  }
};

module.exports = ${ARG1}Controller;
```

## 4. 建立路由
建立 src/routes/${ARG1:kebab}.js:
```javascript
const express = require('express');
const router = express.Router();
const ${ARG1}Controller = require('../controllers/${ARG1}Controller');

router.get('/', ${ARG1}Controller.getAll);
router.get('/:id', ${ARG1}Controller.getById);
router.post('/', ${ARG1}Controller.create);
router.put('/:id', ${ARG1}Controller.update);
router.delete('/:id', ${ARG1}Controller.delete);

module.exports = router;
```

## 驗證步驟:
1. 檢查所有檔案是否正確建立
2. 驗證程式碼語法正確性  
3. 建立基本測試檔案
4. 更新路由註冊

使用方式: `/api:crud Product` 或 `/api:crud UserProfile`
```

#### 步驟3: 建立API測試指令 (10分鐘)
```markdown
# .claude/commands/api-test.md

請為 $ARGUMENTS API建立完整的測試套件。

## 建立測試檔案
建立 src/tests/${ARG1}.test.js:
```javascript
const request = require('supertest');
const app = require('../app');
const ${ARG1} = require('../models/${ARG1}');

describe('${ARG1} API', () => {
  beforeEach(async () => {
    await ${ARG1}.deleteMany({});
  });

  describe('GET /${ARG1:kebab}', () => {
    it('should return empty array when no ${ARG1:kebab} exist', async () => {
      const res = await request(app)
        .get('/${ARG1:kebab}')
        .expect(200);
      
      expect(res.body.success).toBe(true);
      expect(res.body.items).toEqual([]);
    });

    it('should return ${ARG1:kebab} with pagination', async () => {
      // 建立測試資料
      await ${ARG1}.create({ name: 'Test ${ARG1}' });
      
      const res = await request(app)
        .get('/${ARG1:kebab}')
        .expect(200);
      
      expect(res.body.success).toBe(true);
      expect(res.body.items).toHaveLength(1);
      expect(res.body.pagination).toBeDefined();
    });
  });

  describe('POST /${ARG1:kebab}', () => {
    it('should create new ${ARG1:kebab}', async () => {
      const ${ARG1:camel}Data = {
        name: 'Test ${ARG1}',
        description: 'Test description'
      };

      const res = await request(app)
        .post('/${ARG1:kebab}')
        .send(${ARG1:camel}Data)
        .expect(201);
      
      expect(res.body.success).toBe(true);
      expect(res.body.data.name).toBe(${ARG1:camel}Data.name);
    });

    it('should return validation error for invalid data', async () => {
      const res = await request(app)
        .post('/${ARG1:kebab}')
        .send({})
        .expect(400);
      
      expect(res.body.success).toBe(false);
      expect(res.body.error).toBeDefined();
    });
  });

  describe('GET /${ARG1:kebab}/:id', () => {
    it('should return ${ARG1:kebab} by id', async () => {
      const ${ARG1:camel} = await ${ARG1}.create({ name: 'Test ${ARG1}' });
      
      const res = await request(app)
        .get(`/${ARG1:kebab}/${${ARG1:camel}._id}`)
        .expect(200);
      
      expect(res.body.success).toBe(true);
      expect(res.body.data._id).toBe(${ARG1:camel}._id.toString());
    });

    it('should return 404 for non-existent ${ARG1:kebab}', async () => {
      const fakeId = '507f1f77bcf86cd799439011';
      
      const res = await request(app)
        .get(`/${ARG1:kebab}/${fakeId}`)
        .expect(404);
      
      expect(res.body.success).toBe(false);
    });
  });

  describe('PUT /${ARG1:kebab}/:id', () => {
    it('should update ${ARG1:kebab}', async () => {
      const ${ARG1:camel} = await ${ARG1}.create({ name: 'Original Name' });
      const updateData = { name: 'Updated Name' };
      
      const res = await request(app)
        .put(`/${ARG1:kebab}/${${ARG1:camel}._id}`)
        .send(updateData)
        .expect(200);
      
      expect(res.body.success).toBe(true);
      expect(res.body.data.name).toBe(updateData.name);
    });
  });

  describe('DELETE /${ARG1:kebab}/:id', () => {
    it('should delete ${ARG1:kebab}', async () => {
      const ${ARG1:camel} = await ${ARG1}.create({ name: 'To Delete' });
      
      const res = await request(app)
        .delete(`/${ARG1:kebab}/${${ARG1:camel}._id}`)
        .expect(200);
      
      expect(res.body.success).toBe(true);
      
      const deleted${ARG1} = await ${ARG1}.findById(${ARG1:camel}._id);
      expect(deleted${ARG1}).toBeNull();
    });
  });
});
```

## 執行測試
執行測試命令:
```bash
npm test -- --testPathPattern=${ARG1}.test.js
```

使用方式: `/api:test Product`
```

#### 步驟4: 驗證與測試 (5分鐘)
```bash
# 測試指令功能
> 執行 /api:crud User 建立User CRUD API

# 驗證生成的檔案
> 使用LS檢查是否正確建立所有檔案

# 測試API測試指令
> 執行 /api:test User 建立測試檔案

# 執行測試驗證
> 使用Bash執行 npm test 檢查測試是否通過
```

### ✅ Lab完成檢查
- [ ] 成功建立4個API開發指令
- [ ] /api:crud指令能正確生成CRUD API結構
- [ ] /api:test指令能生成完整測試檔案
- [ ] 所有生成的程式碼符合專案規範
- [ ] 測試檔案能正常執行並通過
- [ ] 指令支援參數替換功能
- [ ] 包含適當的錯誤處理機制

### 🚨 Lab故障排除

#### 問題1: 指令參數替換失敗
**症狀**: $ARGUMENTS沒有正確替換
**解決**:
```bash
# 檢查指令檔案語法
> 確認$ARGUMENTS前後沒有多餘空格

# 測試簡單指令
> 建立測試指令: echo "Hello $ARGUMENTS"
```

#### 問題2: 生成的程式碼語法錯誤
**症狀**: ESLint報告語法錯誤
**解決**:
```bash
# 檢查範本語法
> 使用ESLint檢查範本檔案

# 修正語法錯誤
> 調整範本中的JavaScript語法
```

## ✅ M3模組檢核標準
- [ ] 理解Slash指令系統的設計理念與架構
- [ ] 掌握$ARGUMENTS參數系統的使用方法
- [ ] 能建立實用的工作流程指令
- [ ] 能設計參數化的程式碼生成指令
- [ ] 能整合外部工具與API
- [ ] 掌握指令的錯誤處理機制
- [ ] 完成Lab 2的所有實作要求

## 🚨 進階最佳實踐

### 指令設計原則
1. **單一職責**: 每個指令只做一件事
2. **參數驗證**: 提供清楚的參數說明與驗證
3. **錯誤處理**: 包含完整的錯誤處理與回復機制
4. **可組合性**: 指令可以互相組合使用
5. **文檔化**: 提供清楚的使用說明

### 效能優化建議
1. **快取機制**: 快取常用的範本與配置
2. **批次處理**: 支援批次操作減少重複執行
3. **增量更新**: 只更新變更的部分
4. **並行執行**: 支援非相依操作的並行執行

### 安全考量
1. **參數清理**: 防止注入攻擊
2. **權限檢查**: 限制危險操作的執行權限
3. **路徑驗證**: 防止路徑遍歷攻擊
4. **審計紀錄**: 記錄重要操作的執行歷史

## 📖 延伸學習
- [Slash指令進階開發指南](https://docs.anthropic.com/en/docs/claude-code/slash-commands)
- [參數系統完整文檔](https://docs.anthropic.com/en/docs/claude-code/parameters)
- [工作流程自動化最佳實踐](https://docs.anthropic.com/en/docs/claude-code/workflows)
- [API開發完整教學](https://docs.anthropic.com/en/docs/claude-code/api-development)
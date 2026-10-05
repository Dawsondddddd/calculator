# 前后端分离计算器系统

- 后端负责表达式解析、计算、数据校验和数据库操作
- 前端只负责界面交互和结果展示，不做任何计算
- 计算历史保存在后端 SQLite 数据库，刷新或重启前端不会丢失
- 支持删除单条历史记录

## 目录结构

```
calculator/
├── backend/            # 后端项目
│   ├── app.py
│   ├── README.md
│   └── codestyle.md
├── frontend/           # 前端项目
│   ├── index.html
│   ├── README.md
│   └── codestyle.md
└── README.md
```

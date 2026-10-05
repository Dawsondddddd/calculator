# 前后端分离计算器系统（Demo）

一个最小可运行的「前后端分离计算器」示例，对应作业要求：

- 后端负责表达式解析、计算、数据校验和数据库操作
- 前端只负责界面交互和结果展示，不做任何计算
- 计算历史保存在后端 SQLite 数据库，刷新或重启前端不会丢失
- 支持删除单条历史记录

## 目录结构

```
calculator/
├── backend/            # 后端项目（对应一个 GitHub 仓库）
│   ├── app.py
│   ├── README.md
│   └── codestyle.md
├── frontend/           # 前端项目（对应另一个 GitHub 仓库）
│   ├── index.html
│   ├── README.md
│   └── codestyle.md
└── README.md
```

## 技术选型

| 部分 | 技术 | 说明 |
| --- | --- | --- |
| 前端 | 原生 HTML + CSS + JavaScript | 无需框架和构建，打开即用 |
| 后端 | Python + Flask | 提供 REST 接口 |
| 数据库 | SQLite（Python 内置 `sqlite3`） | 单文件数据库，免安装 |
| 表达式解析 | 手写递归下降解析器 | 不使用 `eval` / `exec` |

## 快速开始

需要 Python 3.8+。

1. 安装后端依赖并启动后端：

```bash
cd backend
pip install -r requirements.txt
python app.py
```

2. 另开一个终端启动前端：

```bash
cd frontend
python -m http.server 5500
```

3. 浏览器访问 <http://127.0.0.1:5500>

也可以直接用浏览器打开 `frontend/index.html`。

## 支持的计算

| 用例 | 结果 |
| --- | --- |
| `12+8` | 20 |
| `1+2*3` | 7 |
| `(1+2)*3` | 9 |
| `10/2+7` | 12 |
| `8-3*2` | 2 |
| `-5+8` | 3 |
| `3*-2` | -6 |
| `1.5*2` | 3 |
| `1/0` | 400 错误：除数不能为 0 |
| `1+*2` | 400 错误：表达式格式错误 |

## 接口一览

| 方法 | 路径 | 说明 |
| --- | --- | --- |
| POST | `/api/calculate` | 计算表达式并保存记录 |
| GET | `/api/history` | 查询历史记录 |
| DELETE | `/api/history/{id}` | 删除指定记录 |
| DELETE | `/api/history` | 清空历史记录（附加功能） |

请求示例：

```json
{
  "expression": "(1+2)*3"
}
```

响应示例：

```json
{
  "success": true,
  "id": 1,
  "expression": "(1+2)*3",
  "result": 9,
  "created_at": "2026-10-05 10:20:00"
}
```

## 如何验证前后端确实分离

把后端进程停掉（在运行 `app.py` 的终端按 `Ctrl+C`），此时前端页面仍然可以点击按钮、输入表达式，但点击 `=` 会提示“无法连接后端服务”，不会在前端算出任何结果。

## 注意

本项目是可直接运行的最小实现，两个目录分别对应作业要求的前端仓库和后端仓库。提交时把它们分别推到两个 GitHub 仓库，并在 README / 博客中补充仓库地址与截图即可。

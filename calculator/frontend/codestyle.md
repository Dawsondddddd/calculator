# 前端代码规范

## 规范来源

- [Google JavaScript Style Guide](https://google.github.io/styleguide/jsguide.html)
- [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript)
- [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.html)

## 命名

- 变量和函数使用 `lowerCamelCase`，例如 `expressionInput`、`loadHistory`。
- 常量使用全大写 `UPPER_SNAKE_CASE`，例如 `API_BASE`。
- CSS 类名使用小写加连字符，例如 `history-expression`、`delete-button`。
- DOM 元素的 `id` 使用小写加连字符，例如 `clear-button`。

## 格式

- 使用 2 个空格缩进。
- 语句末尾统一加分号。
- 字符串使用双引号。
- 使用 `const` / `let`，不使用 `var`。
- 文件编码统一使用 UTF-8。

## HTML

- 使用 HTML5 文档类型和 `lang="zh-CN"`。
- 元素语义化，交互按钮使用 `<button>`，列表使用 `<ul>` / `<li>`。
- 输入框添加 `label` 或 `aria-label`，结果区域使用 `aria-live`。
- 样式统一写在 `<style>` 中，按结构、组件、响应式的顺序组织。

## JavaScript

- 使用严格相等 `===` / `!==`。
- 使用 `async` / `await` 处理异步请求，并用 `try / catch` 捕获网络异常。
- 所有网络请求集中通过 `fetch` 调用后端 API，不在前端计算结果。
- 渲染历史记录使用 `createElement` + `textContent`，不拼接 `innerHTML`，避免 XSS。
- 回调函数使用具名函数或带注释的匿名函数，避免过深嵌套。

## 安全与职责

- 前端只负责界面与交互，表达式解析和计算全部由后端完成。
- 后端返回的错误信息原样展示给用户，不在前端伪造结果。
- 不在前端保存计算历史，历史数据始终从后端接口读取。

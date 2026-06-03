# 小组PK擂台赛战报

> 一个单页面数据看板，无需服务器，直接部署到 GitHub Pages 即可使用。

---

## 目录结构

```
pk-dashboard/
├── index.html      # 页面（样式和逻辑都在里面，不用改）
├── data.json       # 数据文件（每天改这个）
└── README.md       # 说明文档
```

---

## 每天更新的方法

**只需要修改 `data.json` 这一个文件。**

打开 `data.json`，按以下字段填写：

| 字段 | 说明 | 示例 |
|------|------|------|
| `period` | 月份标识 | `"2026-06"` |
| `dateRange` | 日期范围 | `"2026-06-01 至 2026-06-30"` |
| `totalMatches` | 总擂台数 | `128` |
| `totalRevenue` | PK净收总金额 | `20315831`（纯数字，不要¥） |
| `totalOrders` | 总订单数 | `9094` |
| `defendWins` / `attackWins` | 守擂/攻擂成功场数 | `86` / `42` |
| `defendRate` / `attackRate` | 守擂率/攻擂率 | `67.2` / `32.8` |
| `currentKing` | 当月王者信息 | 姓名、单数、净收、退款率、战力 |
| `leaderboard` | 个人战力排行榜 | 数组，每人一个对象 |
| `matches` | 焦点擂台 | 数组，每场一个对象 |

---

## 部署步骤（GitHub Pages）

### 第一步：创建 GitHub 仓库

1. 打开 [github.com](https://github.com)，注册/登录
2. 点击右上角 `+` → `New repository`
3. 仓库名填 `pk-dashboard`（或任意名字）
4. 选择 **Public**（公开，GitHub Pages 免费）
5. 点击 `Create repository`

### 第二步：上传文件

在仓库页面，点击 **"uploading an existing file"** 链接，然后：

1. 把 `index.html` 和 `data.json` 拖到页面上
2. 下方填写提交信息：`initial commit`
3. 点击 `Commit changes`

### 第三步：开启 GitHub Pages

1. 仓库页面 → 点击 `Settings`（顶部标签）
2. 左侧菜单 → `Pages`
3. `Source` 选择 `Deploy from a branch`
4. `Branch` 选择 `main` / `master`，点击 `Save`
5. 等待 1-2 分钟，页面会显示你的网址：`https://你的用户名.github.io/pk-dashboard/`

### 第四步：日常更新

以后每天只需要：

1. 打开仓库 → 点击 `data.json`
2. 点击右上角 `✏️`（编辑按钮）
3. 修改数据
4. 页面下方填 `Update data for 6月2日`，点击 `Commit changes`
5. 等 30 秒，刷新网页，数据就更新了

---

## 扩展功能（可选）

如果想让页面更完整，可以补充：

- **火力曲线**：在 `data.json` 里加 `dailyTrend` 数组，页面里用图表库渲染（推荐 [Chart.js](https://www.chartjs.org/)，也是单文件引入）
- **科目分布**：加 `subjectDistribution` 数据，做饼图
- **搜索/筛选**：加 `<input>` 和 `<select>`，用 JS 过滤 `matches` 数组
- **更多擂台**：`matches` 数组里加更多对象，页面会自动渲染

---

## 本地预览（可选）

双击 `index.html` 可以直接在浏览器打开，但因为浏览器安全限制，可能会提示加载 `data.json` 失败。解决方法：

**方法一**：装 VS Code，装 `Live Server` 插件，右键 `index.html` → `Open with Live Server`

**方法二**：临时把 `data.json` 的内容复制粘贴到 `index.html` 里的 `<script>` 里（替换 `fetch` 那部分）

---

## 数据格式参考

```json
{
  "period": "2026-06",
  "dateRange": "2026-06-01 至 2026-06-30",
  "totalMatches": 128,
  "matchesWithResult": 120,
  "totalRevenue": 20315831,
  "totalOrders": 9094,
  "defendWins": 86,
  "attackWins": 42,
  "defendRate": 67.2,
  "attackRate": 32.8,
  "currentKing": {
    "name": "王振彬",
    "orders": 71,
    "revenue": 142000,
    "refundRate": 5.1,
    "power": 14.2
  },
  "leaderboard": [
    { "rank": 1, "name": "王振彬", "orders": 71, "power": 14.2, "revenue": 142000 }
  ],
  "matches": [
    {
      "id": "A001",
      "groupName": "原1组",
      "result": "守擂成功",
      "defender": { "name": "张三", "manager": "N2 李四", "revenue": 100000, "orders": 50 },
      "attacker": { "name": "王五", "manager": "N2 李四", "revenue": 80000, "orders": 40 },
      "module": "学习顾问",
      "lead": 20000
    }
  ]
}
```

---

有问题随时问。

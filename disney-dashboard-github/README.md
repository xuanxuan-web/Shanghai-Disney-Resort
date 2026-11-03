# 迪士尼轨交到达客流数据看板（GitHub Pages 部署包）

一个**完全离线、可交互**的网页看板，可视化上海迪士尼轨交 OD 到达客流（2025 五一，含 2024 同比）。
所有图表与上海 16 区地图都已内联，**不依赖任何网络或外部瓦片**，上传到 GitHub 即可直接打开。

## 包内容

```
disney-dashboard-github/
├── index.html            # 看板主页面（已内联 GeoJSON 与全部数据）
├── assets/
│   └── echarts.min.js     # 本地 ECharts 库（相对路径引用）
├── .nojekyll              # 关闭 Jekyll 处理，确保静态文件原样托管
└── README.md              # 本说明
```

> 注意：本包**不含** surge 的 `CNAME` 文件，不会绑定任何自定义域名，可直接用于 `*.github.io`。

## 部署到 GitHub Pages（三步）

### 方法一：网页上传（最简单，无需 Git）
1. 登录 GitHub，新建仓库（Repository），名字随意，例如 `disney-metro-dashboard`，**勾选 Public**。
2. 进入仓库 → **Add file → Upload files**，把本包里的 `index.html`、`assets/` 文件夹、`.nojekyll` 全部拖进去（保持目录结构，`assets/echarts.min.js` 要在 `assets/` 下）。
3. 提交后，打开仓库 **Settings → Pages → Build and deployment → Source 选 "Deploy from a branch"**，Branch 选 `main`（或你上传的分支），目录选 `/ (root)`，点 Save。
4. 等待约 1 分钟，访问：`https://<你的用户名>.github.io/<仓库名>/`

### 方法二：Git 命令行
```bash
git clone https://github.com/<用户名>/<仓库名>.git
cd <仓库名>
# 把本包里的 index.html、assets/、.nojekyll 复制进来
git add -A
git commit -m "add disney dashboard"
git push
# 再到 Settings → Pages 开启（同方法一步骤 3）
```

## 使用须知
- 看板支持**年份切换（2025 / 2024 / 对比）**、**地图三模式（OD 飞线 / 热力 / 仅站点）**、**TOP-N 滑杆**、**线路筛选**、**点击联动**。
- 数据口径：2025 为 05-01 09 时 TOP100 OD（201 人次 / 95 站 / 15 线 / 12 区）；2024 为同期基线（398 人次 / 284 站）。两年榜单截断口径不同，同比以头部 TOP 与结构占比为准。
- 如需改数据或图表，源码见同级目录 `迪士尼看板源码/`。

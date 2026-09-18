# 教学服务课表网站

一个可直接部署到 GitHub Pages 的静态课表网站，界面按照所提供的截图制作。项目不依赖框架或构建工具，上传后即可运行。

## 已预置的课表信息

| 课程 | 星期 | 节次 | 时间 | 地点 | 周次 |
|---|---|---|---|---|---|
| 微观经济学 | 周一 | 第3—5节 | 10:00—12:35 | 东海岸-E教338 | 第3—18周 |
| 计量经济学 | 周二 | 第3—5节 | 10:00—12:35 | 东海岸-E教307机房 | 第3—18周 |
| 专业认知 | 周一 | 第8—9节 | 16:00—17:40 | 东海岸-E教419-阶梯 | 第3—18周 |

学期第1周从 **2026年9月7日** 开始，共20周。初始页面同时展示第2周和第4周，以复现截图效果。

## 网站功能

- 可同时选择多个周次查看课表。
- 自动标记当前教学周。
- 可添加、编辑和删除课程。
- 自动检查课程时间冲突。
- 修改内容自动保存在浏览器本地存储中。
- 可下载完整课表 JSON 数据。
- 支持电脑与手机屏幕。

## GitHub Pages 部署

### 方法一：从分支部署

1. 在 GitHub 新建仓库，例如 `course-schedule`。
2. 将本项目全部文件上传到仓库根目录并提交到 `main` 分支。
3. 打开仓库的 **Settings → Pages**。
4. 在 **Build and deployment** 中选择 **Deploy from a branch**。
5. Branch 选择 `main`，目录选择 `/ (root)`，然后保存。
6. 发布完成后，访问：

```text
https://你的GitHub用户名.github.io/course-schedule/
```

### 方法二：使用本项目自带的 GitHub Actions

1. 打开仓库的 **Settings → Pages**。
2. 将 Source 设为 **GitHub Actions**。
3. 推送代码后，`.github/workflows/deploy.yml` 会自动发布网站。

## 修改学期与课程

主要数据位于 `assets/app.js`：

```js
const SEMESTER_START = "2026-09-07";
const TOTAL_WEEKS = 20;
const DEFAULT_COURSES = [/* 课程数据 */];
```

直接修改以上配置后重新提交即可。网站上线后，也可以使用“添加课程”按钮在浏览器中调整课表。

## 本地预览

可以直接双击 `index.html`，也可以在项目目录运行：

```bash
python -m http.server 8000
```

然后在浏览器访问 `http://localhost:8000`。

# 赛博养鱼 · CYBER AQUARIUM

[中文](#cn) · [English](#en)

一个单文件的像素风养鱼小游戏：喂食、清藻、用药、买鱼、摆造景，看鱼群在霓虹水族箱里慢慢长大。

A single-file pixel aquarium game: feed your fish, scrub algae, treat the sick, buy new fish, and arrange plants and props while your school grows in a neon tank.

![开始界面 / Start screen](start-panel.png)

<a id="cn"></a>
## 中文

### 玩法

- 开局 3 条鱼、100 起始资金，每 5 分钟结算一次收益。
- 鱼会饿，水质会变差；水质过低会长藻斑，鱼也会生病（头顶出现红十字）。
- 喂食让鱼恢复饱食度；清理擦掉藻斑、拉回水质；用药治好病鱼。
- 商店可以买鱼、买水草/造景，造景模式里把库存拖进鱼缸；造景会影响水质与收益。
- 进度自动保存在浏览器 `localStorage`，关掉页面再打开会接着上次的鱼缸。
- 页面开着时自动挂机：切到别的标签页也计时，离开多少轮就补多少轮收益（每 5 分钟一轮）；水质、饱食、生病与老化按半速推进，单次最多补 8 小时，回到前台会弹一条结算提示。
- 界面支持中文 / English 切换：开始面板与游戏内 HUD 都能切，选择会记住，不影响当前进度。

> 当前为 **Demo 版**，稳定性修复后的预览发布。规则补充：全缸覆没后 60 秒内重新打开并点「抢救鱼缸」，鱼会以病危状态回来（并附赠 1 瓶鱼药），超过 60 秒则按判死进入结算；刷新页面不会免费复活，也不会清掉藻斑和粪便，脏污程度与下一次生成时间会原样续上（水中未吃完的散饵不保存）。

### 按键

| 按键 | 功能 |
| --- | --- |
| `F` / `空格` | 喂食，撒饵后鱼会游过来吃 |
| `C` | 清理：拖动海绵擦掉缸壁藻斑 |
| `Q` | 用药：点击头顶红十字的病鱼 |
| `B` | 商店：买鱼、药水、水草与造景 |
| `D` | 造景：从库存把水草/摆件拖进鱼缸 |
| `R` | 造景模式下旋转摆件 |
| `Esc` | 退出商店 / 造景模式 |
| 鼠标 | 点鱼查看状态，界面按钮也可直接点击 |

### 本地打开

不需要安装任何依赖，也不需要联网：

1. 下载本仓库；
2. 双击 `index.html`，用 Chrome / Edge / Safari 打开即可。

如果浏览器对本地文件有限制，可以起一个静态服务：

```bash
cd cyber-aquarium
python3 -m http.server 8080
# 然后打开 http://localhost:8080
```

### 演示视频

| 文件 | 规格 | 用途 |
| --- | --- | --- |
| `aquarium-demo.mp4` | 1920×1080 · 30fps · 42.7s | 横屏完整演示：进入鱼缸 → 喂食近景 → 商店买鱼与铁皇冠 → 造景入缸 → 清理（脏→净）→ 用药治病 → 收益结算 → 落版 |
| `aquarium-demo-vertical.mp4` | 1080×1920 · 30fps · 29.9s | 手机竖屏分享版，节奏更快，原生竖屏布局实机录制 |

两版都是实机录屏。音轨（city pop 器乐 + 水下环境声 + 交互音效）为程序合成，未使用第三方版权素材。

### 技术说明

- 单文件 HTML + Canvas 2D 像素渲染，无构建步骤、无运行时依赖。
- 横屏/竖屏自适应布局，桌面与手机浏览器都能玩。
- 存档与最佳成绩保存在 `localStorage`，清除站点数据会重置鱼缸。

<a id="en"></a>
## English

### Gameplay

- Start with 3 fish and 100 credits; income settles every 5 minutes.
- Fish get hungry and water quality drops. Low water quality grows algae and makes fish sick (look for the red cross above them).
- Feed to restore fullness, scrub algae off the glass to bring water quality back, and use medicine to cure sick fish.
- The shop sells fish, medicine, plants and decorations. In Decor mode, drag items from your inventory into the tank; decorations affect water quality and income.
- Progress autosaves to browser `localStorage`, so closing the page and coming back picks up where you left off.
- Idle farming while the page stays open: time keeps counting even when you switch tabs. Every 5-minute round you were away is paid in full, while water quality, fullness, sickness and aging advance at half speed (up to 8 hours per catch-up). A summary pops up when you return.
- The interface switches between 中文 and English from the start panel or the in-game HUD. Your choice is remembered and does not reset the current run.

> This is the **Demo build**, a preview release with the stability fixes included. Extra rules: if the whole tank dies, reopen the page within 60 seconds and press "RESCUE" to bring your fish back in critical condition (with 1 free medicine); after 60 seconds the run is settled as a loss. Reloading never revives fish for free and never cleans algae or poop—dirt levels and the next algae spawn timer carry over exactly as they were (uneaten food in the water is not saved).

### Controls

| Key | Action |
| --- | --- |
| `F` / `Space` | Feed; fish swim over to eat the pellets |
| `C` | Clean: drag the sponge to scrub algae off the glass |
| `Q` | Treat: click a sick fish with the red cross above it |
| `B` | Shop: buy fish, medicine, plants and decorations |
| `D` | Decor: drag plants and props from your inventory into the tank |
| `R` | Rotate the selected prop in Decor mode |
| `Esc` | Leave the shop / Decor mode |
| Mouse | Click a fish to inspect it; all on-screen buttons are clickable too |

### Run it locally

No dependencies and no internet connection required:

1. Download this repository.
2. Double-click `index.html` and open it in Chrome, Edge or Safari.

If your browser restricts local files, serve the folder instead:

```bash
cd cyber-aquarium
python3 -m http.server 8080
# then open http://localhost:8080
```

### Demo videos

| File | Spec | What it shows |
| --- | --- | --- |
| `aquarium-demo.mp4` | 1920×1080 · 30fps · 42.7s | Full landscape walkthrough: enter the tank → close-up feeding → buying a fish and a Java fern → placing decor → cleaning (dirty to clean) → treating a sick fish → income settlement → end card |
| `aquarium-demo-vertical.mp4` | 1080×1920 · 30fps · 29.9s | Faster vertical cut for phone sharing, recorded on the native portrait layout |

Both videos are real screen recordings. The audio (city pop instrumental, underwater ambience and interaction sounds) is synthesized in code; no third-party copyrighted material is used.

### Technical notes

- Single-file HTML with Canvas 2D pixel rendering; no build step and no runtime dependencies.
- Responsive landscape and portrait layouts for desktop and mobile browsers.
- Saves and best scores live in `localStorage`; clearing site data resets the tank.

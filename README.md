# 🍉 合成大西瓜·VR版

基于 [shizwd/watermelon-merge](https://github.com/shizwd/watermelon-merge) 二次开发的合成游戏。

开局读取项目里的 `elements/`：12 个角色的图片、名字和合成音效会跟着仓库一起分发。浏览器里的预设只存在本机，不会跟着下载走。

用浏览器直接打开项目里的 `index.html` 即可游玩。需要带上同级的 `elements/` 和 `music/`，不要只拷贝这一个 HTML 文件。

## ✨ 功能特色

### 🎯 玩法

- 左右拖动顶部元素，松开后垂直掉落
- 两个相同等级的元素碰撞后，合成下一级
- 新掉落的元素从第 1 到第 5 级里随机出现，第 6 级及以后只能靠合成
- 已经松开的元素顶部越过虚线并停留 3 秒，判定失败，弹出「游戏失败」，可点「🍃 新一局」
- 还没松开、停在虚线上方的那个元素不算失败

### 🎨 元素

- 左侧栏标题是「元素设置」
- 每一级可以改名、上传图片、上传合成音效，或重置回表情
- 图片只接受 PNG、JPG（`.jpeg` 也算 JPG）
- 合成音效只接受 MP3、WAV
- 格式不对会弹出提示，这张文件不会被用上
- 也可以用压缩包批量导入、导出 1 到 12 的图片，压缩包里同样只收 PNG 和 JPG

### 💾 浏览器预设

- 「保存为预设」把当前 12 级的名字、图片、音效存进这台浏览器
- 一开始有六个槽位，点「＋ 增加槽位」可以继续加
- 已经存过的槽位右边有垃圾桶，只删除这一条浏览器记录
- 刷新页面会回到 `elements/` 里的那一套，不会自动套用预设



### 🖼️ 背景

- 可更换游戏背景，只接受 PNG、JPG
- 可恢复默认背景



### 🎵 音乐播放器

- 内置歌曲：`Virtual to LIVE`
- 添加本地音乐时只接受 MP3、WAV，文件名不能包含中文
- 可粘贴音频链接，可播放、暂停、切歌、拖进度、调音量
- 循环模式：列表循环、单曲循环、随机播放
- 可打开音乐网站弹窗



## 📦 当前这 12 级

编号越小，元素越小。图片放在 `elements/images/`，合成音效放在 `elements/sounds/`，名字写在 `elements/pack.js`。


| 编号  | 名字      | 图片       | 合成音效     |
| --- | ------- | -------- | -------- |
| 1   | mitiya  | `1.png`  | `1.mp3`  |
| 2   | harei   | `2.png`  | `2.mp3`  |
| 3   | liko    | `3.png`  | `3.mp3`  |
| 4   | hazel   | `4.png`  | `4.mp3`  |
| 5   | mizuki  | `5.png`  | `5.mp3`  |
| 6   | sumire  | `6.png`  | 无        |
| 7   | sui     | `7.jpg`  | `7.mp3`  |
| 8   | ameki   | `8.png`  | `8.mp3`  |
| 9   | viridis | `9.png`  | `9.mp3`  |
| 10  | siori   | `10.png` | `10.mp3` |
| 11  | mofu    | `11.jpg` | `11.mp3` |
| 12  | joi     | `12.png` | `12.mp3` |


某一级没有图片时显示表情。没有音效时，这一级合成不发声。`pack.js` 里写了 `.png`，文件夹里实际是同编号的 `.jpg` 或 `.jpeg` 时，页面也会读到。

## 📁 项目结构

```
watermelon-merge/
├── index.html
├── elements/
│   ├── pack.js
│   ├── images/          # 1.png … 12.png，也可以是 jpg
│   └── sounds/          # 1.mp3 … 12.mp3，可以缺
├── music/
│   └── Virtual to LIVE - covered by VirtuaReal_哔哩哔哩_bilibili.mp3
└── README.md
```

换一套开局内容时，按编号替换图片和音效，再改 `elements/pack.js` 里对应的 `name`。例如：

```javascript
{ name: 'mitiya', image: 'elements/images/1.png', sound: 'elements/sounds/1.mp3' },
```

内置背景音乐在 `index.html` 的 `BUILTIN_SONGS`：

```javascript
const BUILTIN_SONGS = [
    { name: 'Virtual to LIVE', url: 'music/Virtual to LIVE - covered by VirtuaReal_哔哩哔哩_bilibili.mp3' },
];
```



## 🚀 放到 GitHub Pages

公开仓库可以免费使用 GitHub Pages。

1. 把整个项目推到你自己的仓库，包含 `elements/` 和 `music/`
2. 打开仓库 **Settings → Pages**
3. Source 选 `Deploy from a branch`，分支选 `main`，文件夹选 `/ (root)`
4. 等一两分钟，打开 `https://你的用户名.github.io/仓库名/`



## 🕹️ 操作说明


| 操作         | 说明                |
| ---------- | ----------------- |
| 拖动顶部元素     | 按住左右移动，松开后掉落      |
| 点击预览图或「上传」 | 给这一级换图片           |
| 点击「音效」     | 上传这一级合成时播放的音频     |
| 点击「重置」     | 这一级恢复为表情          |
| 修改名称       | 改左侧这一级的名字         |
| 导入压缩包      | 按 `1` 到 `12` 批量换图 |
| 导出压缩包      | 把当前图片打包下载         |
| 更换背景图片     | 上传 PNG 或 JPG 背景   |
| 保存为预设      | 把当前一套存进浏览器槽位      |
| 点预设名       | 读出这一槽             |
| 点垃圾桶       | 删除这一槽在浏览器里的记录     |
| 点歌曲或播放键    | 播放列表中的音乐          |




## 🛠️ 技术栈

- **HTML5 Canvas** — 画面
- **Matter.js** — 碰撞与合成
- **JSZip** — 导入、导出压缩包
- **IndexedDB** — 浏览器里的预设
- **Audio** — 背景音乐和合成音效



## ⚠️ 注意事项

- 预设、本地上传的音乐，只在保存它们的那一个浏览器里
- 手动添加的音乐链接需要对方允许跨域，否则播不了
- 内置音乐和角色素材请确认你有权随项目发布
- GitHub 单文件限制 100MB



## 📄 License

MIT License

## 🙏 致谢

- 本项目基于 [shizwd/watermelon-merge](https://github.com/shizwd/watermelon-merge) 二次开发，感谢原作者提供的游戏框架与可玩版本
- [Matter.js](https://github.com/liabru/matter-js) — 2D 物理引擎
- [JSZip](https://github.com/Stuk/jszip) — 前端 ZIP 处理
- 灵感来源于「bilibili.com/video/BV1eEgj6hER9/?spm_id_from=333.337.search-card.all.click」


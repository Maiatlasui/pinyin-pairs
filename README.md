# Pinyin Pairs · 拼音对对碰

面向刚开始学中文的外国大学生的英文界面网页游戏。纯 HTML、CSS、JavaScript，无需安装依赖、注册账户或后端。

## 立即试玩

双击 `index.html` 即可打开。保留 `app.js`、`audio-sources.js`、`style.css` 的相对位置。发音需要联网。也可以在此文件夹运行 `python3 -m http.server 8000`，访问 `http://localhost:8000`。

点击两个完全相同的拼音（字母和声调均相同）即可消除，成功时播放普通话音频。不是需要连线且不超过两次转弯的传统连连看；所有可见牌都可以配对。点同一张牌取消选择。支持键盘 Tab、Enter / Space、静音、重听、重新开始、自由选关和本地通关记录。没有计时或惩罚。

## 关卡

每关 16 张牌 / 8 对，两组音节各包含四个声调。糖果盒棋盘内有四种彩色立体形状，配对时播放闪光消除动画。相同拼音始终使用相同颜色与形状；当前四种颜色对应四声，但仍需字母和声调完全相同才能消除。

| 阶段 | 关卡 | 韵母 | 音节 |
|---|---|---|---|
| 1 单韵母 | 1 | a、o | ma、bo |
| 1 单韵母 | 2 | e、i | ge、mi |
| 1 单韵母 | 3 | u、ü | du、ju |
| 2 双元音组合 | 4 | ei、ai | fei、bai |
| 2 双元音组合 | 5 | ao、ou | mao、hou |
| 2 双元音组合 | 6 | ia、ie | jia、xie |
| 3 三元音组合 | 7 | iao、iou（写作 iu） | jiao、liu |
| 4 鼻韵母 | 8 | an、en | han、fen |
| 4 鼻韵母 | 9 | ang、eng | fang、peng |
| 4 鼻韵母 | 10 | in、ing | lin、qing |
| 5 带介音的鼻韵母 | 11 | ian、iang | tian、xiang |
| 5 带介音的鼻韵母 | 12 | uan、uang | huan、huang |

每个关卡用两个带声母的完整音节，各练四声。ju 的韵母为 ü，j 后省略两点；iou 加声母后写作 iu。ian 虽有三个字母，但以 n 收尾，因此不归入三元音组合。这是渐进式入门路径，未覆盖全部汉语韵母。分类参考：[香港理工大学韵母分组](https://www.polyu.edu.hk/bepth/introduction-to-phonetics/compound-finals/compound-final-groups/)。

菜单按五阶段折叠展示，所有关卡仍可自由选择。新版进度使用单独的本地存储键，旧版六关的完成记录不会错误对应到新关卡，也不会删除旧记录。

## 放到 GitHub Pages

1. 创建一个用于此游戏的 GitHub 仓库。
2. 将**本文件夹里面的文件**上传到仓库根目录：`index.html`、`style.css`、`app.js`、`audio-sources.js` 和 `.nojekyll`。不要只上传 ZIP。
3. 在仓库 Settings → Pages 中，选择从分支部署，选择 `main` 分支和 `/ (root)`，保存。
4. 部署完成后，使用 Pages 页面显示的网址分享给学生，通常是 `https://你的用户名.github.io/仓库名/`。

也可以放到现有站点的子目录，所有资源均使用相对路径。此交付未连接或推送你的 GitHub 账户。

## 音频来源

游戏现在直接播放 [Yoyo Chinese 拼音表](https://yoyochinese.com/chinese-learning-tools/Mandarin-Chinese-pronunciation-lesson/pinyin-chart-table) 的录音，已经停用系统合成音。`audio-sources.js` 记录每个拼音和声调对应的公开音频地址；96 个映射都来自该拼音表实际使用的配置，未猜测地址。

- 必须联网。Yoyo 服务不可用、限制外部播放或修改地址时，游戏会显示重试提示，不会回退到合成音。
- 页面注明 Yoyo Chinese 来源并链接原始拼音表。
- 当前 ZIP 只包含代码和外部音频链接，不包含 Yoyo 音频文件，也不包含之前的合成音文件。工作目录中旧的 `audio/` 仍保留，但游戏不再引用它。
- 署名和公开可访问不等于取得再分发许可。未获得 Yoyo 的音频再分发授权，也未确认其允许第三方网站长期嵌入；公开发布前应向其确认使用范围。来源条款：https://yoyochinese.com/terms

页面使用可选的 Google Fonts；加载失败时回退到系统字体。进度只存储于当前浏览器 localStorage。游戏不收集学生身份信息或上传成绩；在线字体和音频请求会连接相应第三方服务。

## 验证

已验证 12 关、每关 8 对、每组四声覆盖、96 个音频映射齐全。全部 96 个来源地址返回成功状态和音频类型。浏览器检查配对后 Yoyo 录音的播放启动与重听；这不代表完成了逐音人工教学听审。之前已验证配对、通关、阶段菜单和窄屏布局。

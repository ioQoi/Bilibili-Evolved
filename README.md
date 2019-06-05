# Bilibili Evolved
增强哔哩哔哩Web端体验: 下载视频, 音乐, 封面, 弹幕; 自定义播放器的画质, 模式, 布局; 自定义顶栏, 删除广告, 使用夜间模式; 以及增加对触屏设备的支持等.

- [安装](#安装) / [English](install-tutorial.en-US.md) / [インストール](install-tutorial.ja-JP.md)
- [设置](#设置)
- [功能](#功能)
- [兼容性](#兼容性)
- [版本历史与更新日志](https://github.com/the1812/Bilibili-Evolved/releases)
- [投喂](donate.md)

# 安装
需要浏览器拥有[Tampermonkey](https://tampermonkey.net/)插件.

点击名称即可安装👇

| [正式版](https://github.com/the1812/Bilibili-Evolved/raw/master/bilibili-evolved.user.js) | [预览版](https://github.com/the1812/Bilibili-Evolved/raw/preview/bilibili-evolved.preview.user.js) | [离线版](https://github.com/the1812/Bilibili-Evolved/raw/master/bilibili-evolved.offline.user.js) | [预览离线版](https://github.com/the1812/Bilibili-Evolved/raw/preview/bilibili-evolved.preview-offline.user.js) |
| ----------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| 正式发布的版本, 最稳定, 更新频率较低.                                                     | 新增内容测试的地方, 更新频率高, 但功能不稳定.                                                      | 内置所有依赖项, 体积较大, 更新频率高于正式版.                                                     | 兼备预览版和离线版的特点.                                                                                      |

> 某些破坏性的大更新会使旧版脚本**完全**无法工作, 请及时检查更新.
# 设置
脚本启用后, 在网页左侧中央会有一个齿轮图标, 点击即可打开设置.
设置项的说明见[功能](#功能)一节.

**绝大部分设置保存后, 需要刷新网页才能生效. 仅有一些样式设置可以立即生效.**
![设置](images/compressed/gui-settings.jpg)

# 功能
大部分功能可通过设置面板开启, 有一些功能会以`附加功能`的形式生效, `附加功能`可从网页左侧中央的功能按钮进入.
> 为保证最佳体验, 设备分辨率建议在1080P及以上, 并且已登录哔哩哔哩账户.

## 视频
### 下载视频
在视频播放页面中, `下载视频`按钮将在`附加功能`中启用, 点击可以选择清晰度并下载.

#### 注意事项
- 请尊重视频原作者的版权.
- 下载后的格式通常为`.flv`, 若需要`.mp4`格式则要手动用其他软件转换.
- **分段**的视频会把所有视频打包成`.zip`格式.
- 能够下载的清晰度取决于当前登录的账号, 例如`高清 1080P60`需要已登录大会员账号.
- 如果以您的账号权限无法观看某些视频(地区限制, 大会员专享等), 那么这种视频也是无法下载的.
- 下载过程中所有数据都存在内存里, 内存占用很大的话会导致系统卡顿. 如果你更喜欢使用其他的下载软件, 可以使用`复制链接`选项. **下载时的请求Header必须包含`Origin=https://www.bilibili.com`和`Referer=https://www.bilibili.com`**, 直接粘贴在浏览器里是打不开的. [详细信息](https://github.com/the1812/Bilibili-Evolved/wiki/使用下载视频的复制链接)
- 针对上一条, 也可以使用我另外编写的[下载器](extras/video-link-downloader/README.md)解决内存占用问题.
- Chrome浏览器对单个文件大小有[限制](https://chromium.googlesource.com/chromium/src/+/master/storage/browser/blob/README.md#example-limits), 如果在下载完成时浏览器发生崩溃, 请尝试适当降低画质, 或换用没有限制的Firefox浏览器.
    - 64位限制: 2GB
    - 32位限制: 614MB

### 下载弹幕
在视频播放页面中, `下载弹幕`按钮将在`附加功能`中启用, 点击可以下载XML格式的弹幕.
> 点击时若按住`Shift`将下载ASS格式的弹幕, 此功能尚未完善, 完善后会跟XML的操作方式互换.

### 查看封面
在视频播放页面/直播间中, `查看封面`按钮将在`附加功能`中启用, 点击可以查看或保存封面. (其实还可以看专栏的封面, 不过专栏的封面本来就显示在标题上方了)

![查看封面/下载视频/下载弹幕](images/compressed/download-video-view-cover.jpg)

### 指定播放器布局
设置默认的播放器布局, 可分别设置视频区和番剧区. 尽量在相应的页面里设置(比如在番剧播放页面设置番剧播放器布局), 否则可能没有效果.

> **⚠ 旧版布局中, 很多脚本功能将不适用.**

- 旧版: 传统布局
- 新版: 视频区默认的新版布局

### 默认播放器模式
设置默认的播放器模式, 可以为`常规`, `宽屏`, `网页全屏`或`全屏`. 可以选择在进入页面的首次播放时应用, 或者一进入页面就应用. 还可以设置是否自动关灯.
<!--
> ⚠ 自动全屏的稳定性还有待观测, 目前仅有一定概率成功. 如果它在您的电脑上没有效果, 那么请无视这个`全屏`选项吧.
-->
### 默认视频画质
进入视频时自动选择指定的画质, 若视频最高画质低于所选画质, 则使用视频的最高画质.

> 官方于2018.12.27已正式支持记忆画质
### 默认弹幕设置
设置默认是否开启弹幕, 以及是否记住防挡字幕和智能防挡弹幕.
### 自动展开弹幕列表
新版播放页面中, 弹幕列表默认收起以显示推荐的其他视频. 启用此功能可在每次加载视频时自动展开弹幕列表.
### 自动展开视频简介
长的视频简介默认会被折叠, 启用此功能可以强制展开完整的视频简介.
### 自动从历史记录点播放
播放视频时如果检测到历史记录信息(`上次看到...`消息), 则自动跳转到相应的时间播放.
> 如果还开启了`允许跨集跳转`, 即使当前集数跟历史记录不同也会跳转.

### 自动播放视频
进入视频页面时自动开始播放视频.
### 跳过充电鸣谢
自动跳过视频结尾处的充电鸣谢.
### 启用逐帧调整
在播放器的时间右边增加两个按钮, 用于**较**精细调整视频时间. 支持键盘快捷键`Shift + 左/右方向键`. (旧版播放器只能用键盘快捷键, 不会显示按钮)

注: `视频的实际播放帧率`跟`视频本身的帧率`和`显示器的刷新率`有关, 很难计算一个精准的数值, 部分视频仍然会有暂停不到那种一闪而过的图的情况.

逐帧调整的精确度固定为:
- `1080P60`/`720P60`: 1001 / 60000 秒 (59.94006 fps)
- `其他清晰度`: 1001 / 30000 秒 (29.97003 fps)

### 启用视频截图
在播放器的时间右边增加截图按钮, 点击可以截取视频画面, 不会包含暂停标志和弹幕. 截取的图片将在网页右侧显示(非全屏或网页全屏模式), 可以单独保存或丢弃, 也可以截取一定数量后一次性保存. 支持键盘快捷键`Ctrl + Alt + C`. (旧版播放器只能用键盘快捷键, 不会显示按钮)

![时间右边的按钮](images/compressed/control-enhance-buttons.jpg)

### 自动定位到播放器
进入视频/番剧页面时, 自动定位到播放器.

### 外置稍后再看
将视频页面菜单里的`稍后再看`移到外面.

![外置稍后再看](images/compressed/watchlater.jpg)

## 样式
### 主题颜色
设定顶栏和夜间模式使用的主题色, 可以点击颜色预览的圆圈打开色板, 其中含有预定义的16种主题色, 也可以在右侧的文本框直接输入任何有效的16进制颜色值(`#rrggbb`或`#rgb`).

![颜色设置](images/compressed/theme-color.jpg)
<!-- ![粉色](images/compressed/new-navbar-stardust.jpg)
![紫色](images/compressed/new-navbar-purple.jpg)
![蓝色](images/compressed/new-navbar-lightBlue.jpg)
![绿色](images/compressed/new-navbar-teal.jpg)
![暗蓝色](images/compressed/new-navbar-blueGrey.jpg)
### 样式调整
**主要**会改变顶栏的样式, 并有一些其他地方的界面微调:
- 为播放器增加主题色投影
- 可控制顶栏对横幅的透明度
- 使播放器按钮垂直对齐
- 使部分搜索栏的提示文字的颜色更清晰
- 隐藏播放页面的"返回旧版"侧栏
- 修复直播间一些文字初始状态不正确
- 窄屏幕下强制保留弹幕发送栏

**顶栏效果**
![主站](images/compressed/new-navbar.jpg)
![播放](images/compressed/new-navbar-stardust.jpg) -->
### 自定义顶栏
启用自定义顶栏, 替代原版的顶栏, 仅对主站生效, 直播/相簿/会员购等仍使用原来的顶栏.

可用的选项包括:
- 使用主题色填充顶栏
- 使用主题色填充其他的顶栏, 包括直播/相簿/会员购等
- 为顶栏添加一层阴影效果
- 为顶栏使用更紧凑的布局, 紧凑布局将使用更小的间距, 以及在视频标题过长时用...省略后面的部分
- 在顶部横幅存在时, 使用背景模糊效果
- 设定背景模糊效果的不透明度
- 改变顶栏边缘两侧的间距
- 改变顶栏里栏目的顺序和显示状态

前6个是整体的外观设置, 可以在设置里直接开关, 后面2个是对顶栏里面内容的详细布局设定, 可以在`附加功能`里设置.

下图展示了顶栏在不同设置下的整体外观: (从上到下依次为: 不使用主题色填充, 不填充+夜间模式, 填充主题色, 使用不同的主题色)
![效果图](images/compressed/custom-navbar-effects.jpg)

顶栏内容的布局也可以自定义, 可以通过此功能移除顶栏里不需要的组件, 或排列它们的顺序:
![顶栏顺序自定义](images/compressed/custom-navbar-orders.jpg)


### 夜间模式
夜间模式更适合光线暗的环境, 并会大量应用主题颜色.

目前仅支持部分常用页面, 其他页面会陆续添加, 不支持推广板块(会被`删除广告`功能去除的部分).

**启用前**
![日间](images/compressed/light-style.jpg)

**启用后**
![夜间](images/compressed/dark-style.jpg)

#### 夜间模式计划时段
设置一个使用夜间模式的时间段, 进入/离开此时间段时, 会自动开启/关闭夜间模式.
> 结束时间小于起始时间时将视为次日, 如`18:00`至`6:00`表示晚上18:00到次日6:00.
### 首页使用紧凑布局(实验性)
设置首页是否使用紧凑布局, 视频的间距会减小并削去圆角, 番剧的图片和排名序号会变成圆形, 分区栏的图标会使用高清重制版. 目前仅支持首页, 其他分区的样式后续会添加.

**启用前**
![原版布局](images/compressed/compact-layout-disabled.jpg)

**启用后**
![紧凑布局](images/compressed/compact-layout.jpg)

### 简化评论区
- 删除热评头像下方的关注按钮
- 删除用户的等级标识
- 删除发送源信息(`来自安卓客户端`这种)
- 删除用户名右边的勋章
- 发送时间移动到右上角
- 位图图标全部换用矢量图标, 高分屏不会模糊
- 投票仅显示链接, 隐藏下面的大框.

> 关注和等级可以通过鼠标停留在头像上, 在弹出的资料卡小窗中查看

![简化评论区](images/compressed/comments.jpg)

### 简化直播间
- 隐藏姥爷图标
- 隐藏粉丝勋章
- 隐藏活动头衔
- 隐藏用户等级
- 隐藏舰长图标
- 隐藏全区广播
- 隐藏欢迎信息 (xxx姥爷进入直播间)
- 隐藏抽奖提示 (开通舰长, 小飞船抽奖等)
- 禁用直播间皮肤

每一项都可以在`附加功能`中单独选择是否隐藏. 图片中展示的是全部隐藏时的效果对比.

![简化直播间](images/compressed/simplify-liveroom.jpg)

<!-- ### 搜索栏置顶
在主站中总是把搜索框置于顶栏, 如果页面里没有搜索栏则不会显示. 仅对常用页面有效, 部分页面可能会有点布局错乱.

**启用前**
![不调整](images/compressed/original-navbar.jpg)

**启用后**
![调整](images/compressed/override-navbar.jpg) -->

### 隐藏顶部横幅
隐藏主站顶部的横幅, 注意这会导致搜索框也被隐藏, 除非开启了自定义顶栏.
<!--
#### 显示排行榜图标
在搜索栏置顶启用的时候, 还可以使用此功能显示/隐藏排行榜入口.
![排行榜图标](images/compressed/ranklist.jpg) -->
### 播放器投影
为播放器添加主题色投影.

### 强制保留弹幕发送栏
在网页全屏时, 即使宽度过小也强制保留弹幕发送栏, 注意这可能导致右侧的功能按钮挤出边界.

### 模糊视频控制栏背景
模糊视频控制栏背景, 原版的阴影效果将无效.
此功能需要浏览器支持背景模糊效果, 详情见[兼容性](#兼容性)一节.

**启用前**
![不模糊背景](images/compressed/original-control.jpg)

**启用后**
![模糊背景](images/compressed/blur-video-control.jpg)

### 控制栏着色
给视频控制栏附上半透明的黑色, 代替原来的阴影, 黑色的不透明度可在设置中调整.

**启用前**
![原版](images/compressed/original-control.jpg)

**启用后**
![着色](images/compressed/custom-control-background.jpg)

### 缩放直播看板娘
根据屏幕DPI缩放直播看板娘的大小以提高像素的清晰度, DPI缩放为100%的用户不需要此功能.
### 删除直播水印
删除观看直播时角落的水印.
### 删除视频标题层
删除视频里鼠标经过时出现在右上角的标题层.
![覆盖层](images/compressed/remove-top-mask.jpg)
### 隐藏返回旧版
隐藏播放页右侧的`返回旧版`入口.
### 隐藏番剧点评
隐藏番剧播放页面的点评板块, 不会隐藏番剧介绍页那里的点评.

## 工具
### 删除广告
删除站内的各种广告. 包括首页的推广模块, 手机app推荐, 视频页面右侧的广告等.
![删除广告](images/compressed/remove-ads.jpg)
### 稍后再看重定向
将稍后再看的链接重定向为普通播放网址, 以使用新版播放页面.
### 收藏夹视频重定向
将个人空间收藏夹里的视频重定向为直链, 而不是收藏夹播单链接.
### 隐藏搜索推荐
将搜索框的推荐词替换为`搜索`.
### 展开动态标题
在顶栏的动态预览框中, 不管名称多长, 总是完全展开视频的标题.
![展开动态标题](images/compressed/full-tweets-title.jpg)
### 展开选集标题
在视频选集列表中, 当标题超出一行时, 另起一行以显示完整标题.
> 因为番剧选集用的绝对布局, 所以此功能在番剧区无效.

![展开选集标题](images/compressed/full-page-title.jpg)
### 直播间勋章快速切换
在直播区(live.bilibili.com)中, 可从`附加功能`中直接切换勋章和头衔.
### BiliPlus跳转支持
在视频/番剧/空间中, 附加功能`转到BiliPlus`, 点击可以转到[BiliPlus](https://biliplus.com)上对应的页面.
### 下载音频
在音频区中, 附加功能会出现`下载音频`按钮, 当你进入某一音乐的详细信息页面时, 点击按钮可以下载该页面对应的音乐. 在其他页面中此按钮将不可点击.

> 正在播放的音乐点击封面即可转到详细信息页面.

### 高分辨率图片
根据屏幕DPI请求更高分辨率的图片, 例如DPI缩放200%则请求2倍的分辨率, 加载时间也会相应变长一些.
适用于2K, 4K等的显示屏, DPI缩放为100%的用户不需要此功能.

![image-resolution](images/compressed/image-resolution.jpg)

### 旧版动态跳转支持
将新版动态的链接换为旧版动态, 同时可在附加功能中在新旧动态间切换.

### 界面翻译(实验性)
为界面中一些常用文本提供翻译, 目前仅开放日语和英语.

## 触摸
### 顶栏
删除顶栏右侧的一级链接(从`大会员`到`历史`), 以方便触屏设备快速预览信息. 被删除的链接可从各预览中的`查看更多`进入.
### 素质三连
为素质三连(长按点赞)启用触摸支持.
### 播放器
- 增大控制栏的按钮间距, 使触摸操作更准确.
![放大前](images/compressed/player-buttons-original.jpg)
![放大后](images/compressed/player-buttons-large.jpg)
- 启用触摸手势
    - 左右滑动可调整进度
    - 上下滑动可调整音量
    - 进度调整可在左上角和右上角取消
    - 在不同位置滑动, 可以使用3档不同的灵敏度.

![触摸调整](images/compressed/touch-player.gif)
#### 启用双击控制
将操作方式更改为: 单击显示/隐藏控制栏, 双击播放/暂停.

## 其他
关于脚本自身的一些设定.
### 显示消息
允许在网页左下角显示来自本脚本的消息, 如更新提醒, 错误提示等.
![消息](images/compressed/toast.jpg)
#### 显示内部错误消息
开启后, 错误消息将显示详细的技术性错误信息及堆栈跟踪, 这通常用于准确地确定问题发生的原因, 所以报告问题时这些信息会非常有用.
### 启用缓存
使用缓存以提高脚本的加载速度, 此选项只对非离线版有效, 可在`附加功能`中清除脚本的缓存.
### 文件命名格式
自定义文件命名格式, 作用于`下载弹幕`, `下载视频`, `视频截图`, `查看封面`.
可以使用的变量有:
- `title`: 视频标题/直播间标题
- `ep`: 选集标题
- `aid`: AV号
- `cid`: CID (每个视频的唯一编号, AV号对应的视频可能有多集)
- `lid`: 直播间号
- `y`/`M`/`d`: 年/月/日
- `h`/`m`/`s`/`ms`: 时/分/秒/毫秒

默认的格式是`[title][ - ep]`, 标题+选集标题, 当没有选集标题时则只有标题.

变量要放在方括号里, 而方括号里的其他内容会在变量有效时出现. 比如格式如果写成`[title] - [ep]`, 那么即使没有选集标题, 中间那个` - `也会出现在文件名里. 如果像默认那样放在方括号里, 没有选集标题时, ` - `也不会出现.

例如, 想要标题+AV号+时间的格式, 可以设定为`[title][ AVaid] [y]-[M]-[d] [h]-[m]-[s]`, 能够得到类似`xxxx AV23333 2019-05-29 19-59-44`的名字.

# 兼容性
## 脚本管理器
### [Tampermonkey](https://tampermonkey.net/) / [Violentmonkey](https://violentmonkey.github.io/)
完全兼容.
### [Greasemonkey](https://www.greasespot.net/)
不支持, 请使用以上的两种管理器.

## 浏览器
> ⚠ 不保证脚本能在["套壳类浏览器"](https://www.jianshu.com/p/67d790a8f221)中完美运行.

### Chrome / Edge (Chromium)
- 背景模糊效果([backdrop-filter](https://developer.mozilla.org/en-US/docs/Web/CSS/backdrop-filter))需要手动在`chrome://flags/#enable-experimental-web-platform-features`中开启. (Edge要把`chrome`换成`edge`)
- 含有背景模糊效果的动画有掉帧现象.
- 在Chrome ≥ 73版中, 如果您的屏幕DPI缩放大于100%, 或者改动了页面缩放倍数, 则模糊效果区域会错位. 详见[Chromium Issue #942910](https://bugs.chromium.org/p/chromium/issues/detail?id=942910).
### Firefox
- 背景模糊效果无效, 详见[Bugzilla #1178765](https://bugzilla.mozilla.org/show_bug.cgi?id=1178765).
- 触摸调整的进度预览有弹跳现象.(源自CSS `transition`. 短时间内总是从原数值开始变化, 而不是当前数值)
### Safari
- 尚未在Safari中测试.(流下了贫穷的泪水
### Edge (UWP) [**停止支持**]
- 请使用以上列出的浏览器, 或换用 [Chromium 内核的 Edge](https://microsoftedgeinsider.com/).

**喜欢的话就点个⭐Star吧(°∀°)ﾉ**

[返回顶部](#Bilibili-Evolved)
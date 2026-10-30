# 灵想剧创 项目记忆

## 关键约定
- 用户给的尺寸都是 **1920 设计稿标注值**，助手负责用 `clamp(最小值, 设计稿值/1920*100vw, 设计稿值)` 自动适配其他屏宽。
- Header / Hero / CanvasBanner：全宽 + 动态左右 padding `clamp(40px, 10.625vw - 96px, 108px)`（1920=108px，1280=40px 保证 1200 内容区）。
- `.container` 全局类 ≤1366px 时左右 padding 30px。
- 图片资源前缀：`https://dyanyapi.elecottech.com/h5_static_img/LXJC/`。

## CardStack（三卡）版本状态 —— 两个可切换版本
用户会在「静态三卡」和「环形卡堆」两者之间选择，切换命令如下：
- 说「**还原静态三卡**」→ 用 `.workbuddy/memory/CardStack-静态三卡版本.vue.bak` 覆盖 `src/components/home/CardStack.vue`。
- 说「**还原到环形卡堆**」→ 用 `.workbuddy/memory/CardStack-环形卡堆版本.vue.bak` 覆盖 `src/components/home/CardStack.vue`。

**静态三卡版本**：纯静态阶梯式三卡，中间卡带文字、左右卡纯图变暗，无轮播逻辑。
**环形卡堆版本**：参考「环形差值 + 位形表」方案（位移+scale，无 rotate 倾斜）。三卡环形循环轮播，中间卡满大带文字（453×427），左右卡 scale 0.73 缩小变暗、向两侧位移 ±260px、内侧被中间卡压住、各露出约 5/6。拖拽跟手（侧卡 0.6 阻尼）+ 松手 >60px 切换，无需克隆卡（ringDiff 折叠）。

## 卡片尺寸（1920 设计稿）
- 中间卡：453×427，圆角 27，背景 #09141A，padding 16px
- 左右卡：331×333，圆角 24，背景 #08141A，padding 16px
- card-label margin-top 14px；card-play 24×24，与 card-title 底边对齐（align-self: flex-end）
- 播放按钮图：`paly2Icon.png`

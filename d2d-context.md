# d2d-context

## 基本信息
- 设计链接：https://www.figma.com/design/NTBeaNDTAbeIVB9OxlmNOp/%E9%BD%90%E5%90%9B-%E4%B8%93%E4%B8%9A%E8%B5%84%E6%BA%90%E5%BA%93%E8%8D%89%E7%A8%BF?node-id=380-19573
- fileKey：NTBeaNDTAbeIVB9OxlmNOp
- 根节点：380:19573（"设计页面"，column 布局，宽 1920px）
- 素材目录：/Users/chenjiao/Downloads/专业资源库/文件
- 输出目录：/Users/chenjiao/Documents/Qoder/2026-08-24/chat-1/

## 全局样式
- 页面背景色：#0E202E + 4层径向渐变（黄绿 C9F80A 辉光 + 黑色暗角）
- 主字体：Alibaba PuHuiTi 3.0（非系统字体，需 mdfind 检查）
- 副字体：PingFang SC、Microsoft YaHei
- 主题色：#C9F80A（黄绿）
- 卡片背景：rgba(255,255,255,0.05) + backdrop-filter:blur(25px)
- 毛玻璃容器：rgba(8,17,25,0.44) + backdrop-filter:blur(100px) + border-radius:50px

## 模块骨架表

| # | 模块名 | 节点ID | 类型 | top(px) | 高(px) | 备注 |
|---|--------|--------|------|---------|--------|------|
| 1 | 首屏 | 460:12868 | 绝对定位 | 0 | 900 | CUSTOM paint 无法读取，整卡切图入槽（首屏-视频.mp4 + 首屏-logo.png + 首屏-动态智能体.png） |
| 2 | 主内容区 | 460:13389 | 绝对定位 | 900（与首屏重叠/紧接） | 4880 | 含全部子模块，背景多层径向渐变+#0E202E |
| 2a | 专业概况 | 460:13391区域 | column | top≈119 | ~500 | 左文右图，活写文本 |
| 2b | 课程中心 | 460:13496 | column | top=551(相对主内容区) | hug | 毛玻璃容器，3卡片，悬停态 |
| 2c | 题库中心 | 460:13533 | column | top=1357 | hug | 分类 tabs + 2行×3卡片 |
| 2d | 专业介绍 | 460:13404 | column | top=2113 | hug | 毛玻璃容器，左右切换+教师轮播 |
| 2e | 数字教材 | 460:13462 | column | top=3173 | hug | 左文 + 右书封面组 |
| 2f | 虚拟展厅 | 460:13451 | column | top=3855 | hug | 标题+大图+侧边菜单 |
| 3 | 底部 | 460:13556 | row | top=4740(相对主内容区) | hug | logo+版权链接行 |

## 素材映射预判

| 文件 | 尺寸 | 用途 |
|------|------|------|
| 首屏-视频.mp4 | ~25MB | 首屏背景视频 |
| 首屏-动态智能体.png | ~41MB | 首屏右侧装饰大图 |
| 首屏-logo.png | ~14KB | 首屏顶部 Logo |
| 专业概况-配图.png | ~1.5MB | 专业概况模块右侧图（节点 460:13568，800×400） |
| 虚拟展厅配图.png | ~3.2MB | 虚拟展厅大图（节点 460:13454） |
| 底部配图.png | ~1.4MB | 底部背景装饰图（节点 460:13390，opacity 0.16） |
| 底部- logo.png | ~42KB | 底部 Logo（节点 460:13557，500×40） |

## 执行观测
- 2026-08-31 步骤1完成：Framelink 读骨架成功（首屏节点 CUSTOM paint 报错，其余正常）
- 首屏节点 460:12868 含 CUSTOM paint type，Framelink 无法解析，改为整卡切图方案
- figma.py 主路径暂不可用（Python3/Xcode CLI Tools 未安装），全程走 Framelink 兜底路径

## 2026-09-07 课程中心模块重构（设计稿已更新）

- 左边数据（节点 460:13510）：宽 236、设计高 370（实现改 align-self:stretch 与卡片等高，实测 374px 全等）；column + space-between；6 条数据项，每项 236×48、padding 0 24、gap 20、白5%底、1.5px 绿 0.2 边、圆角 4、blur25
  - 数据：28门课程 / 6门专业核心课 / 8门标准化课程 / 8门标课程已建知识图谱 / 8份教学标准 / 48期课程总期数
  - 数字：D-DIN Bold 700 18px rgba(201,248,10,0.8)；标签：PuHuiTi 55 Regular 16px rgba(255,255,255,0.7)
- 3 张卡片（460:13529/13530/13531）：padding 24、column gap 20；图高 240 fill；标题 PuHuiTi 65 Medium 20px 白0.9 字距0.04em；元数据行 space-between
  - 元数据：左组 gap16（14学时|3学分|10期，数字 D-DIN Bold 18px 绿0.8、标签 16px 白0.7、对内 gap6、分隔线 1×18 白0.1）+ 右"专业核心课" 16px 白0.7
  - 卡片1 默认 配图1 自动驾驶系统原理；卡片2 悬停态 配图2 车联网与智能交通 固定宽 427 绿边+阴影+blur10；卡片3 默认 配图3 新能源汽车动力系统
- 行容器（460:13509）：row gap30 align stretch（树为 center，改 stretch 保证侧栏与卡片严格等高）；卡片1/3 flex:1 各约 423.5px
- 字体：新增 @font-face D-DIN 400/700（fonts/D-DIN.otf、D-DIN-Bold.otf，拷自 ~/Library/Fonts）
- 验证：浏览器实测侧栏=3卡=374px 顶底完全对齐；卡片2 宽 427px；截图 course-center-verify.png

## 2026-09-07 专业介绍模块重构（教师信息卡片）

- tabs（460:13408）：专业师资（激活 #C9F80A 黑字）/ 专业荣誉 / 历史沿革 / 专业资讯热点；容器 1279 宽，查看更多 absolute right:0
- 内容行（460:13417）：row justify-center gap80 宽 1600 = 大切换左 80 + 卡片 1280 + 大切换右 80（切图按钮）
- 教师信息卡片（460:13419）：1280×442 固定，row padding40 gap60，白5%底、1px 绿0.1 边、blur25、圆角4
  - 左列（460:13420）宽 866 column gap30：张明远（PuHuiTi 85 Bold 30px 白）
  - 信息行（EL-ae004bd9）：row padding16 0 gap40 align-center，下边框 1px 白0.12；图标(20/20/18=3x切图) + gap20 + 标签(16 Medium 白0.95) + 值(16 Regular 白0.8)
    - 研究方向=智能驾驶系统、车载传感器技术、自动驾驶算法；职称职务=教授，博士生导师；教师简介=长文本 line-height 1.75em justify
  - 教师照片（460:13435）：272×360（源 544×720@2x），object-fit fill，圆角 4
- 轮播（460:13437）：13 头像 space-between 宽 1600；默认环 padding6+80×80 圆(93px)白10%底白0.05 边；激活(460:13443)渐变环 137deg 绿→蓝 + 100×100(116px)
- 验证：卡片 1280×442 / 照片 272×360 loaded / 左列 866 / 13 头像(80/100) / 无溢出；截图 intro-top.png、intro-bottom.png

## 2026-09-07 间距修正 + DOM 嵌套修复 + 本地化

- **DOM 嵌套 bug（根因）**：卡片3 第二个 meta-div 写成 `<div class="meta-div"></span>`（开 div 闭 span），1 个未闭合 div 导致题库中心/专业介绍/数字教材/虚拟展厅全部嵌套进课程中心 inner-sec（课程中心高度异常 4253px、入场动效双重位移、间距错乱）。已修为 `<span class="meta-div"></span>`，node 解析验证：6 模块全部顶层、div 开闭平衡归零。
- **数字教材**（树 460:13462 padding-left 160 / fill）：inner-sec padding `0 0 80px 100px`→`0 0 80px 160px`；内部容器去 `width:1860px` 改 fill（内容宽 1760）；书组 `justify-content:flex-end;flex:1`→`flex-shrink:0` 自然宽（卡片684+gap57+书组≈1213 溢出右缘被 scale-wrap 裁掉，对应参照图书"partially visible"）。
- **虚拟展厅**：展厅首页大图 `flex:1`→`width:1260px;flex:none` 固定宽（用户点名）。
- **间距实测**（清 transform 后，1x 坐标）：专业概况→课程中心 92.3（树绝对定位：专业概况 y=100、内容容器 y=551，间隙≈92 ✓）；课程中心→题库中心 80 ✓（用户确认值）；题库→专业介绍 80；专业介绍→数字教材 80；数字教材→虚拟展厅 80（树「内容」容器 gap=80 全吻合）。
- **本地化**：assets/ 引用切图 46/46 就位（83M），index-local.html 打开 0 破损图，自包含可离线分发。
- 测量方法教训：inner-sec 的 getBoundingClientRect 含 padding-bottom，模块盒间恒 0；须测相邻模块 firstElementChild 之间的空隙。

## 2026-09-08 课程中心/题库中心悬停交互修正

- **课程中心**：`.card` 增加 `:hover` 规则与 `.active` 共享（100% 主题色边框 + 绿色投影 + blur(10px)）；去掉卡片 2 硬编码 `active` 类，默认态全部 20% 边框，hover 才高亮。
- **题库中心**：`.qcard` 增加 `:hover` 规则；去掉第一张题卡硬编码 `active`；修正题型标签颜色（判断题→blue，多选题→yellow）；底部元数据改为截图样式「难度：易 + 课程：汽车智能技术 + 驾驶 + 智能汽车」。
- **验证**：桌面版截图确认课程中心/题库中心卡片 hover 均出现绿色边框+投影，其余卡片保持默认；题库新文案生效。
- **未改**：课程中心 tabs 文字当前仍为「推荐课程/标准课程/培训课程/双创课程」，设计截图显示为「全部/专业核心课/专业基础课/专业必修课」，待用户确认是否更新。

## 2026-09-08 专业介绍教师轮播交互

- **需求**：点击左右箭头或下方头像切换教师信息，样式不变，照片与头像联动，补假信息。
- **实现**：
  - 数据驱动：JS 数组 `teachers` 含 5 位教师（张明远/李婉清/王志强/陈思雨/刘建华），字段：name/research/title/bio/photo。
  - 上方卡片元素加 id（teacher-name/research/title/bio/photo），左右箭头加 id（teacher-prev/next）。
  - 下方头像加 class `t-avatar` + `data-teacher` 索引；active 状态控制渐变环、头像尺寸 80→100、圆角 93→116。
  - 左右箭头点一下切一位并循环；头像点击直接定位。
- **验证**：
  - 点击右箭头：张明远→李婉清，照片1→照片2，高亮头像位置 6→1 ✓
  - 点击第 4 个头像：→刘建华，高亮头像位置 4 ✓
- 未做头像整体滚动居中，只做了高亮状态切换（按沟通方案）。

## 2026-09-08 修复教师照片切换 URL 编码 bug

- **问题**：`photoEl.src.replace(/\d+\.png$/, t.photo+'.png')` 在 file:// URL 编码中把 `%E7%89%87`（片）的 `87` 与 `1.png` 一起识别为 `871.png` 并替换为 `3.png`，导致 URL 编码损坏、图片 naturalWidth=0。
- **修复**：给 `#teacher-photo` 加 `data-base-src` 属性存无编号路径，JS 直接拼接 `data-base-src + photo + '.png'`，绕开正则。
- **验证**：切换后 `decodedSrc=.../assets/专业介绍-教师照片3.png`，naturalWidth=544，naturalHeight=720，图片正常显示。

## 2026-09-08 补充专业介绍 13 位教师资料

- **内容**：将教师轮播从 5 位扩展到 13 位（对应照片 1–13），为每位补充姓名、研究方向、职称、假简介；给照片 6–13 的头像补 `data-teacher` 属性。
- **照片显示问题**：照片 12/13 因桌面版未同步导致未显示，同步后验证 naturalWidth=544、naturalHeight=720，加载正常。
- **简介 4 行对齐**：经浏览器实测逐位调整 bio 长度，最终 13 位教师 `#teacher-bio` 均为 clientHeight=112px / lineHeight=28px，恰好 4 行。

## 2026-09-08 诊断照片12/13不显示

- **复测结果**：浏览器实际检测 13 张教师头像均 complete=true、naturalWidth=544、naturalHeight=720；Console 无 404；点击第 13 个头像后大照片正确切到 `专业介绍-教师照片13.png`。
- **结论**：文件和代码均正常，用户侧不显示为浏览器缓存导致。
- **建议**：使用带版本号的 URL `index.html?v=14` 强制刷新；必要时清空浏览器缓存后再打开。

## 2026-09-08 数字教材模块轮播交互（6本）

- **实现**：左侧书名/作者/出版社/简介/页码随当前选中封面联动；右侧 6 张封面点击或左右箭头切换，当前封面放大到 203×300 + 主题色边框+阴影，其余保持 240px 高 + 半透明边框。
- **数据**：补充 6 本假教材信息（书名、作者、出版社、简介）。
- **验证**：点击第 3 个封面 → 书名="汽车发动机电控系统检修"、current="03"、activeIndex=2、activeWidth=203、activeHeight=300；点击第 6 个封面 → 书名="新能源汽车动力电池及管理系统"、current="06"。

## 2026-09-08 Spotlight 调整 + 题库中心查看更多尺寸

- **Spotlight**：从 1200×1200px 缩小到 720×720px，中心不透明度从 0.10 提高到 0.26，卡片局部描边从 0.55 提高到 0.85，更明显。
- **题库中心查看更多**：切图 261×66 显示 130×33 比其他模块大 50%，按视觉一致性改为 87×22（与课程中心/数字教材/专业介绍统一）。

## 2026-09-08 数字教材简介限制2行 + Spotlight继续弱化

- **数字教材简介**：给 `#book-intro` 加 `height:58px` + `-webkit-line-clamp:2`，验证 clientHeight=58，即 2 行。
- **Spotlight**：从 720×720px 缩小到 520×520px，中心不透明度从 0.26 降到 0.16，卡片描边从 0.55 降到 0.55（与中心亮度匹配），整体更柔和。

## 2026-09-08 数字教材轮播改为滚动式

- **实现**：右侧封面改为统一 203px 宽的 `book-cover-wrap` 容器，当前项始终滚动到左侧主位（203×300 + 主题色边框），其他项保持 240px 高。整组封面通过 `transform: translateX(-idx*243px)` 平移，带 0.5s 缓动动画。
- **交互**：左右箭头切换上一本/下一本；点击右侧任意封面直接滚动该书到左侧主位；左侧书名/作者/出版社/简介/页码同步更新。
- **验证**：点击第 4 个封面 → `translateX(-729px)`、`current=04`、active 封面 203×300；点击左箭头 → `translateX(-486px)`、`current=03`。

## 2026-09-08 虚拟展厅分类切换交互

- **实现**：右侧 4 个菜单项（展厅首页/科学研究/名师风采/专业大数据）点击切换；当前选中项边框变绿、底部进度条变绿、标题高亮；左侧大图淡入淡出切换到对应配图。
- **新增素材**：将 `虚拟展厅-科学研究配图.png`、`虚拟展厅-名师风采配图.png`、`虚拟展厅-专业大数据配图.png` 从下载目录复制到 assets/ 和桌面演示目录。
- **验证**：点击【科学研究】→ 图片切换为 `虚拟展厅-科学研究配图.png`、activeTab=科学研究；点击【专业大数据】→ 图片切换为 `虚拟展厅-专业大数据配图.png`、activeTab=专业大数据。

## 2026-09-08 修复数字教材轮播 stage 缩放问题

- **问题**：`#book-covers` 整体 `transform: translateX(-idx*243px)` 会被 stage 的等比缩放同步缩小，导致视觉上平移距离不足，前面的书仍露出。
- **修复**：改为给第一个 `.book-cover-wrap` 设置 `margin-left: -idx*243px`，子元素相对容器平移不受 stage 缩放影响，当前项准确滚动到容器左边缘。
- **验证**：renderBook(2) 后 wrap0/wrap1 的 inViewport=false（完全隐藏），wrap2 left=coverLeft=301（当前项在容器左边缘）；renderBook(0) marginLeft=0；renderBook(5) wrap5 left=coverLeft=301。

## 2026-09-08 同步最新演示到桌面

- **目标**：`/Users/chenjiao/Desktop/专业资源库演示/`
- **内容**：`index.html`（来自 index-local.html）+ `assets/` + `fonts/`
- **大小**：119M

## 2026-09-18 首屏大图无损压缩 + 上传 GitHub

- **首屏大图**：`assets/首屏-动态智能体.png` 原为 41MB（1000×1000，导出压缩质量异常），用 `sips -s format png` 重编码后 **498KB**，尺寸/alpha/色彩解释不变。像素级验证：两版各自转 BMP 后 `cmp` **逐字节一致** → 无损，放心替换。工作区与桌面演示版均已替换，assets 95M→54M。
- **仓库**：https://github.com/ess205871-droid/professional-resource-library （公开）
- **上传方式**：本机无 git（Xcode CLI Tools 因连不上 Apple 更新服务器安装失败），改用纯 Node 脚本 `.upload-github.cjs` 直连 GitHub Git Data API（blob → tree → commit → 更新 ref）。
- **文件映射**：`index-local.html`（assets/ 相对路径）→ 仓库 `index.html`（可在线预览）；`index.html`（本机 /Downloads 绝对路径）→ 仓库 `index-source.html`（设计源存档）。
- **上传清单**：64 个文件 / 78.6 MB（根文件 4 + assets 54 + fonts 6）。
- **远程校验**：文件总数 64、`index.html` 中 `/Downloads` 引用 0 处、`assets/` 引用 50 处、首屏大图 498KB ✓。
- **在线预览**：GitHub Pages 已开启 → https://ess205871-droid.github.io/professional-resource-library/ ；实测 47/47 图片加载成功、视频 readyState≥1、Console 无 404、首屏 CountUp 正常显示终值。
- **安全**：旧的明文 token 已撤销；新 token 仅经环境变量传给脚本，未落盘、未写入任何文件（项目内 `grep ghp_` 无残留）。

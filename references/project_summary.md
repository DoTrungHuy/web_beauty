# xuanxuan-prompts 项目及提示词总结整理（技术栈索引）

本项目是由 `xuanxuan321` 发起的精美网页复刻提示词合集。每个网页项目都经过了精妙的设计，旨在通过结构化的极细粒度 Prompt，让 Coding Agent（如 Claude Code, Cursor 等）能够 **100% 完美复刻出殿堂级的视觉动效**。

以下是本项目收录的 **10 个网页复刻项目** 的技术解析与使用指南：

---

### 一、 核心项目分类汇总

#### 1. 单文件 HTML 极简运行类（无需任何构建工具，开箱即用）

##### 🌸 项目 [flower] — Veldara 沉浸式滚动发光花朵落地页
*   **技术栈**: 纯原生 HTML/CSS/JS (零第三方依赖，纯手写 Canvas 粒子、SVG 动效，完全不引用 Tailwind/GSAP/Three.js)。
*   **视觉风格**: 深空黑底，一朵盛开的发光花朵作为全屏视频背景，伴随缓慢游走的白色星点粒子。
*   **招牌交互**: **滚动驱动的视频帧（Scroll-Scrubbed Video）**。将滚动条作为视频的时间轴，向上滚动倒回，向下滚动推进。中段包含 3 张卡片，以“固定在视口底部+横向擦除”形式交替出现。
*   **资源直链**:
    *   视频 CDN: `https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260616_212935_bbf608da-62d1-4f25-9be4-c346e4d09cc8.mp4`

##### 🌿 项目 [bloom] — 赛博植物学叙事落地页
*   **技术栈**: 纯原生 HTML/CSS/JS (Google Fonts + 原生 JS `requestAnimationFrame` 驱动)。
*   **视觉风格**: 黑色背景、粉色发光花朵、生物机械质感、高强半透明玻璃拟态卡片（`backdrop-filter: blur(80px)`）、紫色霓虹强调色。
*   **招牌交互**: **多段视频“预抽帧缓存”平滑滚动算法**。页面加载时分别 fetch 3 个 MP4 并转为 Blob URL，通过隐藏的 video 元素和 `createImageBitmap` 提取出高质量帧图缓存，滚动时直接绘制到 Canvas 上，彻底解决实时 Seek 视频造成的画面闪烁和卡顿。
*   **资源直链**:
    *   视频 1: `https://res.cloudinary.com/dsdhxhhqh/video/upload/v1781506095/202606101700_hglz7q.mp4`
    *   视频 2: `https://res.cloudinary.com/dsdhxhhqh/video/upload/v1781506108/202606101702_sd50y0.mp4`
    *   视频 3: `https://res.cloudinary.com/dsdhxhhqh/video/upload/v1781506130/202606101703_jmidj2.mp4`

##### 🌌 项目 [liquidGlass] — 太空旅行电影感落地页
*   **技术栈**: CDN 引入 React 18 + Tailwind CSS + Framer Motion + Babel。
*   **视觉风格**: 黑色科幻，双段视频背景，高光边缘液态玻璃设计系统（`liquid-glass` 与 `liquid-glass-strong` 样式）。
*   **招牌交互**: **原生 JS 驱动的双视频交叉淡入淡出（Crossfade）**。利用 `requestAnimationFrame` 精准控制两个全屏固定视频的 Opacity 渐变，营造极致平滑的星际航行过渡体验。
*   **资源直链**:
    *   Hero 视频: `https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260418_080021_d598092b-c4c2-4e53-8e46-94cf9064cd50.mp4`
    *   Capabilities 视频: `https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260418_094631_d30ab262-45ee-4b7d-99f3-5d5848c8ef13.mp4`

---

#### 2. React + Vite + Tailwind 现代工程类（顶级主流技术栈，适合生产环境）

##### 🏀 项目 [basketball] — Slam Dunk Store 程序化 3D 运动电商单页
*   **技术栈**: React + TypeScript + Vite + Tailwind CSS + Three.js (`@react-three/fiber` / `drei`) + GSAP 动效库。
*   **视觉风格**: 极为硬朗的高端运动科技风，全屏沉浸。
*   **招牌交互**: **3D 程序化球体生成与滚动叙事**。通过 Three.js 纯代码程序化生成一个逼真的 3D 篮球置于页面正中央，随着向下滚动，篮球随叙事线旋转、缩放。包含加购时的飞入购物车特效、球鞋/配件定制器 Modal、抽屉购物车以及轻微的程序化音频反馈。

##### 🖥️ 项目 [liquidGlassAgency] — 深色液态玻璃 AI 网页设计工作室落地页
*   **技术栈**: React + Vite + Tailwind CSS + shadcn/ui + Framer Motion。
*   **视觉风格**: 奢侈品级暗黑美学，全屏电影质感视频背景，超透亮玻璃拟态。通过双层 `::before` 遮罩合成技术（`mask-composite: exclude`），绘制出一圈散发微妙荧光的超薄高光外边框（0.5px - 1px）。
*   **资源直链**:
    *   Hero 视频: `https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260307_083826_e938b29f-a43a-41ec-a153-3d4730578ab8.mp4`
    *   StartSection 视频 (HLS Mux): `https://stream.mux.com/9JXDljEVWYwWu01PUkAemafDugK89o01BR6zqJ3aS9u00A.m3u8`
    *   Stats 视频 (HLS Mux, 去色过滤): `https://stream.mux.com/NcU3HlHeF7CUL86azTTzpy3Tlb00d6iF3BmCdFslMJYM.m3u8`
    *   Footer 视频 (HLS Mux): `https://stream.mux.com/8wrHPCX2dC3msyYU9ObwqNdm00u3ViXvOSHUMRYSEe5Q.m3u8`

##### 👁️ 项目 [blueEyes] — NOVA_AI 视频逐帧滚动极简大字落地页
*   **技术栈**: React + TypeScript + Vite + Tailwind CSS + Lucide React 图标库。
*   **视觉风格**: 滚动视频背景（蓝色光纤汇聚成数字之眼）、配合巨幅硬朗无衬线大字（`Flexo Soft Medium` 字体）。
*   **招牌交互**: 手写高吞吐量 React Canvas 视频预抽帧组件。在组件挂载时将 24fps 视频全部转为 `ImageBitmap` 数组，完美解决浏览器实时 seek 带来的渲染卡顿。
*   **资源直链**:
    *   视频: `https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260611_104107_121bfb5a-b1df-4e0d-8240-25b81f7cc85d.mp4`

##### 🚪 项目 [openDoor] — Unleash The Full Power 沉浸式滑动门视频落地页
*   **技术栈**: React 19 + Vite + Tailwind v4 + GSAP (ScrollTrigger + ScrollTo) + hls.js + react-router-dom。
*   **视觉风格**: 滚动擦洗 HLS 视频背景，液态玻璃材质 About 面板，胶囊药丸导航栏（带 GSAP 驱动的液态高光填充反馈）。
*   **招牌交互**:
    1. **HLS（Mux 直链）平滑滚动定位**：采用 HLS 双向缓冲优化，将视频进度绑定 to 500vh 的超级滚动条中。
    2. **液态胶囊按钮**：当鼠标悬停在导航丸上时，圆形的黑色流体色块从下方融化、扩大并充盈整个胶囊，文字反色为白色。
*   **资源直链**:
    *   HLS H.264 视频流: `https://stream.mux.com/43NlHXsaMrmyzWamMk87m01fNyxSTekAD669BBAPBNm00.m3u8`

##### 🔍 项目 [interactiveDiscovery] — Lithos 地质品牌光标揭示 Hero 页
*   **技术栈**: React + TypeScript + Vite + Tailwind CSS + Lucide 图标。
*   **视觉风格**: 极简科技，暗色背景。
*   **招牌交互**: **光标跟随手电筒滤镜（Interactive Reveal）**。鼠标在屏幕上移动时，会产生一个柔和的圆形探照灯区域。探照灯内部会实时透过第一张图，揭示出背后隐藏的第二张高精度地质扫描/结构剖面图。

---

#### 3. AI 辅助克隆真实站点类（配合高阶 Agent 技能）

##### 🏎️ 项目 [helmet] — 真实网站 Lando Norris 官网复刻
*   **技术栈**: 结合 `website-offline-archive` 离线爬取技能。
*   **内容**: 指引 Agent 爬取 F1 著名车手 Lando Norris 的官网 `landonorris.com` 极具张力的赛车头盔/护目镜 Hero 页面，将其结构和媒体资源无损复刻到本地工程。

##### 🧊 项目 [iceHouse] — 真实网站 Igloo.inc 重度 WebGL 场景复刻
*   **技术栈**: 结合 `website-offline-archive` 技能。
*   **内容**: 完美复刻 `igloo.inc` 的全景 WebGL 3D 冰屋沉浸式互动场景。

---

### 二、 核心精美视觉动效实现“武林秘籍”

#### 1. 液态玻璃（Liquid Glass）高光边框算法 (CSS)
```css
.liquid-glass {
  background: rgba(255, 255, 255, 0.01);
  background-blend-mode: luminosity;
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  border: none;
  box-shadow: inset 0 1px 1px rgba(255, 255, 255, 0.1);
  position: relative;
  overflow: hidden;
}
.liquid-glass::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1.4px; /* 决定高光外边框的粗细 */
  background: linear-gradient(
    180deg,
    rgba(255, 255, 255, 0.45) 0%,
    rgba(255, 255, 255, 0.15) 20%,
    rgba(255, 255, 255, 0) 40%,
    rgba(255, 255, 255, 0) 60%,
    rgba(255, 255, 255, 0.15) 80%,
    rgba(255, 255, 255, 0.45) 100%
  );
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude; /* 关键：抠除内部，只留极细边框 */
  pointer-events: none;
}
```

#### 2. Canvas 视频预抽帧平滑滚动核心架构 (JS)
```javascript
// 初始化缓存所有帧，避免实时 seek
async function cacheVideoFrames(videoUrl, targetFps = 18) {
  const video = document.createElement('video');
  video.src = videoUrl;
  video.muted = true;
  video.playsInline = true;
  video.crossOrigin = 'anonymous';
  await new Promise(resolve => video.onloadedmetadata = resolve);
  
  const duration = video.duration;
  const totalFrames = Math.min(144, Math.round(duration * targetFps));
  const frames = [];
  
  for (let i = 0; i < totalFrames; i++) {
    const time = (i / (totalFrames - 1)) * (duration - 0.02);
    video.currentTime = time;
    await new Promise(resolve => video.onseeked = resolve);
    const bitmap = await createImageBitmap(video, { resizeWidth: 840 });
    frames.push(bitmap);
  }
  return frames;
}
```

# web_beauty - 精美网页复刻 AI 智能助手 Skill

## When to use
当用户需要让 AI 智能体（Agent）复刻极具视觉冲击力、动效丰富、带有电影级质感的现代网页时。例如包含 3D 渲染（WebGL / Three.js）、滚动视频擦洗驱动、液态玻璃拟态、光标跟随遮罩等交互的高端官方落地页或叙事落地页。

## Runtime requirements
- **Browser login required**: no
- **Sandbox required**: yes
- **Page script required**: no
- **User local folder required**: yes (用于存放克隆后的网页项目模板及生成的 `prompt.md` 提示词文件，即 `web_beauty` 目录)

## Capability routing
1. **意图识别**：识别用户喜欢哪个风格的网页（或喜欢哪种高级动效，如 3D 篮球、视频滚动逐帧播放、液态玻璃设计系统、光标跟随等）。
2. **提示词供给**：在技能库 `references/` 目录或用户本地 `web_beauty` 文件夹中快速定位该网页的完整 `prompt.md` 提示词。
3. **本地交付/导出**：将提示词文件、外部 CDN 视频与字体直链以及项目基础框架一并呈献给用户，或直接写入用户的开发工作区。

---

## Workflow

1. **需求匹配**：询问或识别用户想要复刻哪一种精美网页风格（当前支持 10 款顶级高端网页风格）。
2. **提示词提取**：读取对应目录下的 `prompt.md` 复刻提示词（包含所有所需的 HTML/CSS/JS、视频直链、字体及精细组件结构参数）。
3. **代码生成/指导**：
   - 对于**单文件 HTML 项目**，直接帮用户在工作区生成对应的 `.html` 文件，使用浏览器直接打开即可运行。
   - 对于**React + Vite + Tailwind 项目**，自动创建配套的 `package.json` 依赖配置，让用户一键安装运行。
4. **验证与交付**：向用户展示视频和素材直链，以及如何在本地快速起服务预览，确保完美 1:1 复刻。

---

## Files in this skill
- `SKILL.md`: 核心工作流与技能定义
- `references/project_summary.md`: 10 个精美网页项目提示词的索引与技术栈解析汇总
- `mp4-to-gif.sh`: 用于将本地录屏 MP4 高质量转换为预览 GIF 与 Poster 首帧封面的工具脚本

---

## Output contract
每个项目的提示词包必须包含：
- **HTML 单文件** 或 **React/Vite 完整框架包** 的搭建指引。
- 公网可直接访问的 **视频/图片/动画 CDN 直链**（无需翻墙，全球加速）。
- 精细到像素级的 **CSS 样式、液态玻璃（Liquid Glass）高光边框算法、视频帧预抽缓存平滑算法**。

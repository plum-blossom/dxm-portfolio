<script setup>
import { ref, computed, onMounted } from "vue";
import ProjectCard from "./components/ProjectCard.vue";
// 导入 Animate.css
import "animate.css";
// 图片加载函数
const getImage = (fileName, filePath = "/skills") => {
  try {
    return new URL(`${filePath}/${fileName}`, import.meta.url).href;
  } catch (error) {
    console.error(`Failed to load image: ${fileName}`, error);
    return null;
  }
};
// 项目数据
const projects = [
  {
    id: 1,
    title: "网络安全实训靶场前端系统",
    companyProject: true,
    description:
      "设计并开发了一套完整的网络安全实训靶场前端系统，支持网络环境构建、攻防演练、技能评估等功能，服务于网络安全人才培养和实战能力提升。该系统基于 Monorepo 架构，统一管理多个前端项目，包括竞赛活动平台、攻防对抗演练平台、培训实训平台等。",
    image: getImage("rangeHub项目说明截图.png", "/project/rh"),
    images: [
      getImage("rangeHub项目说明截图.png", "/project/rh"),
      getImage("企业脚手架工具说明截图.png", "/project/rh"),
      getImage("自动化测试之e2e.png", "/project/rh"),
      getImage("组件库文档说明截图.png", "/project/rh"),
    ],
    tags: [
      "Vue 3",
      "TypeScript",
      "Vite",
      "Vue CLI",
      "Element Plus",
      "Pinia",
      "Vuex",
      "Vue Router",
      "xterm.js",
      "vis.js",
      "ECharts",
      "WebSocket",
      "Guacamole",
      "Turbo",
    ],
    category: "企业级应用",
    period: "2021.10-2026.03",
    link: "#projects",
    responsibilities: [
      "架构设计与工程优化：采用模块化思想拆分功能模块，设计高内聚低耦合的系统架构",
      "远程桌面连接技术：深度定制修改 Guacamole 源代码，实现 Web 端远程桌面连接功能",
      "Web 终端与网络拓扑：通过 xterm.js 库创建终端实例，结合 WebSocket 实现实时双向通信",
      "AI 智能助教：实现智能助教功能，支持流式响应、Markdown 渲染、代码高亮",
      "多语言支持与国际化：通过 vue-i18n 实现多语言支持",
      "代码质量与性能优化：通过 ESLint、Prettier 等工具建立代码规范",
      "Turbo 增量构建系统：集成 Turbo 构建系统实现增量构建",
      "自动化测试体系：基于 Playwright 搭建端到端自动化测试框架",
      "项目技术选型与基建：负责项目技术栈选型，搭建前端工程化体系",
      "组件库与基础建设：主导团队共享组件库、图表库及基础库的沉淀与文档建设",
      "规范化与配置管理：将项目配置抽离为统一管理，实现配置的集中化和复用",
      "脚手架抽离：抽离 Vue 后台管理系统脚手架，支持 vue-cli 和 vite 两个版本",
    ],
    achievements: [
      "构建了包含地形设计、攻防演练、活动竞赛平台等完整功能的网络靶场平台",
      "支持多租户隔离和权限管理，满足不同用户群体的需求",
      "系统稳定运行于各类网络安全培训和竞赛场景，获得用户好评",
      "实现了攻防证据自动化收集与裁决流程，提高了竞赛评审效率和公正性",
      "封装通用组件库与工具函数，提供统一的技术解决方案",
      "通过 Turbo 增量构建系统，构建效率提升 60% 以上",
    ],
  },
  {
    id: 2,
    title: "指挥控制系统前端",
    companyProject: true,
    description:
      "集成任务规划、态势监控、载荷管理、情报分析等核心功能模块，构建一体化前端操作平台，为军事指挥、网络安全分析、系统运维等场景用户提供统一、高效的交互与业务支撑能力。",
    image: getImage("项目说明截图.png", "/project/zhkz"),
    images: [
      getImage("项目说明截图.png", "/project/zhkz"),
      getImage("三维态势页面.png", "/project/zhkz"),
      getImage("关系图.png", "/project/zhkz"),
      getImage("网络拓扑图.png", "/project/zhkz"),
    ],
    tags: [
      "Vue 3",
      "TypeScript",
      "Vue CLI",
      "Element Plus",
      "Vuex",
      "Vue Router",
      "Three.js",
      "Cesium",
      "Socket.io",
      "ECharts",
      "@antv/g6",
      "xterm.js",
      "crypto-js",
    ],
    category: "3D可视化",
    period: "2024.07-2026.03",
    link: "#projects",
    responsibilities: [
      "3D 态势可视化：协助集成 Three.js 和 Cesium 实现 3D 地球可视化，构建实时态势感知系统",
      "任务规划系统：协助基于@antv/g6 实现任务拓扑图设计，支持任务创建、编辑、载荷配置",
      "可视化图表开发：协助使用 ECharts 实现多维度数据图表展示",
    ],
    achievements: [
      "协助构建了指挥控制系统前端，支持从任务规划到执行、监控、评估的全流程管理",
      "参与实现了 3D 地球可视化、实时态势感知、任务拓扑设计等核心功能",
      "协助开发的可视化功能模块稳定运行于军事指挥场景，获得用户好评",
    ],
  },
  {
    id: 3,
    title: "多端一体化内容管理平台",
    personalProject: true,
    learningTarget: "跨端开发和服务端渲染技术",
    description:
      "为了深入跨端开发和服务端渲染技术,我利用业余时间重写了一个概念版 Demo（见下方链接）。基于 uni-app 实现 App、小程序、H5 三端统一界面与逻辑开发，完成路由管理、状态存储与跨端接口适配；使用 Nuxt4 对原有 Vue 项目进行重构，落地服务端渲染方案，优化首屏加载与 SEO 表现。基于芋道（Yudao）低代码平台完成二次开发：搭建本地前后端环境，通过 Vue3 管理后台定制业务菜单、配置生成参数，编写 SQL 脚本并完成代码包生成；将前端组件、后端代码及数据库脚本集成至项目，验证全链路功能正常，实现业务菜单模块快速落地。",
    image: getImage("报名系统项目说明截图.png", "/project/uni-app"),
    imageClass: "ara",
    images: [
      getImage("报名系统项目说明截图.png", "/project/uni-app"),
      getImage("报名系统H5效果.gif", "/project/uni-app"),
      getImage("报名系统小程序效果.gif", "/project/uni-app"),
      getImage("小程序二维码.png", "/project/uni-app"),
      getImage("演示录屏.gif", "/project/nuxt"),
      getImage("bd-exam项目说明.png", "/project/nuxt"),
      getImage("芋道管理后台.png", "/project/yudao"),
      getImage("芋道后端项目启动.png", "/project/yudao"),
    ],
    tags: ["uni-app", "Nuxt4", "Vue 3", "TypeScript", "Node.js", "Express", "SQLite", "Trae", "芋道（Yudao）"],
    category: "跨端开发",
    period: "2023.01-2026.01",
    link: "#projects",
    demoLinks: [
      {
        name: "uni-app开发的报名系统demo",
        sourceCode: "https://gitee.com/web-dev-summary/enrollment-system.git",
        demoLink: "https://static-mp-a3adac0e-7e7a-46d8-ad79-308e4c769dd5.next.bspapp.com/#/",
      },
    ],
    responsibilities: [
      "基于 uni-app 实现 App、小程序、H5 三端统一界面与逻辑开发",
      "使用 Nuxt4 对原有 Vue 项目进行重构，落地服务端渲染方案",
      "基于 Node.js + Express + SQLite 搭建简易后端服务，实现数据持久化与接口管理",
      "基于芋道（Yudao）低代码平台完成二次开发：搭建本地前后端环境，通过 Vue3 管理后台定制业务菜单、配置生成参数，编写 SQL 脚本并完成代码包生成；将前端组件、后端代码及数据库脚本集成至项目，验证全链路功能正常，实现业务菜单模块快速落地",
      "全程使用 Trae 辅助完成 API 文档生成、代码模板生成与基础逻辑编写",
    ],
    achievements: [
      "实现了多端统一的内容管理平台，支持 App、小程序、H5 三端访问",
      "通过 Nuxt4 重构优化了首屏加载速度和 SEO 表现",
      "完成了前后端全栈开发，实现了完整的业务流程",
      "实现基于芋道（Yudao）低代码平台完成二次开发",
    ],
  },
  {
    id: 4,
    title: "邦道公司业务前端系统",
    companyProject: true,
    description:
      "设计并开发了公司 BD 目录下的多个前端项目，包括会计电算化系统、移动端应用、公司官网和综合管理系统，支持财务处理、移动端交互、企业形象展示和综合业务管理等功能，服务于公司业务发展和数字化转型。",
    image: getImage("bd工作项目成果截图.png", "/project"),
    images: [getImage("bd工作项目成果截图.png", "/project")],
    tags: [
      "Vue 2.6",
      "Vue Router",
      "Vuex",
      "Element UI",
      "Vant UI",
      "ECharts",
      "Less",
      "Axios",
      "Webpack",
      "ES6+",
      "amfe-flexible",
      "postcss-pxtorem",
      "TinyMCE",
      "Vue-Baidu-Map",
      "Vue-Cropper",
      "vuedraggable",
    ],
    category: "企业级应用",
    period: "2019.10-2021.10",
    link: "#projects",
    responsibilities: [
      "技术选型与架构设计：主导公司 BD 业务前端项目的技术选型和架构设计",
      "核心功能实现：实现会计电算化系统的账簿管理、凭证处理、报表生成等核心功能",
      "移动端适配与用户体验：采用 amfe-flexible 和 postcss-pxtorem 实现移动端适配",
      "数据可视化与状态管理：使用 ECharts 实现复杂数据的图表展示",
      "性能优化与代码质量：通过代码分割、懒加载、图片优化等手段提升项目加载速度",
    ],
    achievements: [
      "成功交付会计电算化系统、移动端应用、公司官网和综合管理系统等多个前端项目",
      "提升了团队的开发效率和代码质量，建立了规范的前端开发流程和技术标准",
      "优化了用户体验，提高了系统的可用性和稳定性，获得业务部门的好评",
      "为公司业务发展提供了有力的技术支持，推动了公司数字化转型进程",
    ],
  },
  {
    id: 5,
    title: "天人地科技前端项目集合",
    description:
      "负责开发和维护公司旗下多个前端项目，包括直播平台、公会后台管理系统和公司官网，为用户提供完整的在线服务生态。",
    image: getImage("trd工作项目成果截图.png", "/project/trd"),
    images: [
      getImage("trd工作项目成果截图.png", "/project/trd"),
      getImage("公司官网.png", "/project/trd"),
      getImage("直播官网.png", "/project/trd"),
    ],
    tags: ["jQuery", "LayUI", "CSS3", "Swiper", "RongIMClient", "七牛云SDK"],
    category: "前端开发",
    period: "2019.03-2019.10",
    link: "#projects",
    responsibilities: [
      "直播平台：PC端直播功能、视频流播放、实时聊天、图片视频上传、用户中心、排行榜、礼物系统",
      "公会后台：成员管理、数据统计、财务报表、权限管理、操作日志记录",
      "公司官网：企业形象展示、响应式设计、轮播图效果、页面性能优化",
    ],
    achievements: [
      "项目成功上线并稳定运行，为业务发展提供技术支持",
      "提升用户体验与系统性能，获得用户好评",
      "建立规范的前端开发流程与代码规范",
    ],
  },
  {
    id: 6,
    title: "拍个全景AR平台",
    description:
      "该项目为AR全景实景认证平台，核心包含实景认证后台超级管理系统、多元化营销活动插件（转盘抽奖、微投票、摇一摇、问卷调研、微助力、企业手册制作）、官方移动端网站及配套小程序，为企业提供全景展示、实景认证、营销互动一体化解决方案。",
    image: getImage("项目成果截图.png", "/project/cn"),
    imageClass: "ara",
    images: [
      getImage("项目成果截图.png", "/project/cn"),
      getImage("平台登录.png", "/project/cn"),
      getImage("平台管理.png", "/project/cn"),
      getImage("大转盘.png", "/project/cn"),
      getImage("摇一摇.png", "/project/cn"),
    ],
    tags: ["HTML5/CSS3", "jQuery", "Vue", "Vue-CLI", "ECharts", "Bootstrap", "PS", "PHP", "MySQL", "小程序开发"],
    category: "AR/VR",
    period: "2018.06-2018.12",
    link: "#projects",
    responsibilities: [
      "基于PSD设计稿完成页面切片、布局搭建，实现总平台页面排版与动态交互效果",
      "独立开发全景总平台系统全页面及交互功能，搭建官网移动端Vue开发环境",
      "对接后端接口实现数据交互，基于HTML5、ECharts、PHP+MySQL完成营销插件的开发",
      "参与平台小程序开发，完成实景认证、营销互动等核心模块的页面与功能实现",
    ],
    achievements: [
      "高效完成平台全端页面开发与功能落地，实现全景展示、实景认证、多场景营销互动等核心能力",
      "页面交互流畅、数据交互稳定，支撑平台日常运营与企业用户使用需求",
    ],
  },
  {
    id: 7,
    title: "Git Commit Lint 插件",
    description:
      "开发了一款 VS Code 插件，用于在提交代码前自动检查 Git commit 消息格式，帮助团队规范提交信息，提高代码协作效率。",
    image: getImage("Git Commit Lint Plugin代码截图.png", "/project/vscode-extension"),
    images: [
      getImage("Git Commit Lint Plugin代码截图.png", "/project/vscode-extension"),
      getImage("编译器安装VSCode插件截图.png", "/project/vscode-extension"),
    ],
    tags: ["TypeScript", "VS Code API", "Git", "Extension API", "Node.js"],
    category: "工具开发",
    period: "2023.06-2023.08",
    link: "#projects",
    responsibilities: [
      "插件架构设计：设计插件的整体架构和功能模块，确保插件的可扩展性和可维护性",
      "Git Commit 检查：实现 Git commit 消息格式检查功能，支持多种提交规范",
      "VS Code API 集成：使用 VS Code Extension API 实现插件与编辑器的深度集成",
      "用户界面开发：开发友好的用户界面，提供实时反馈和错误提示",
    ],
    achievements: [
      "成功开发并发布 VS Code 插件，帮助团队规范 Git commit 消息格式",
      "插件安装量和使用率逐步提升，获得用户好评",
      "提升了团队代码协作效率，减少了因提交格式不规范导致的沟通成本",
    ],
  },
];

// 技能数据
const skills = [
  // 前端核心
  {
    name: "HTML5",
    icon: "🌐",
    category: "前端核心",
    description: "语义化HTML5，响应式布局与移动端适配",
    image: getImage("HTML5.svg"),
  },
  {
    name: "CSS3",
    icon: "🎨",
    category: "前端核心",
    description: "CSS3高级特性，Flexbox、Grid、动画过渡",
    image: getImage("CSS3.svg"),
  },
  {
    name: "JavaScript",
    icon: "🟨",
    category: "前端核心",
    description: "ES6+特性，异步编程，DOM操作",
    image: getImage("javascript.svg"),
  },
  {
    name: "TypeScript",
    icon: "📘",
    category: "前端核心",
    description: "类型定义与推断，提升代码可维护性",
    image: getImage("typescript.svg"),
  },
  {
    name: "Vue 2/3",
    icon: "⚡",
    category: "前端核心",
    description: "Vue 2/3生态，组件化开发",
    image: getImage("Vue.svg"),
  },
  {
    name: "Vue Router",
    icon: "🔗",
    category: "前端核心",
    description: "路由管理与导航守卫",
    image: getImage("Vue.svg"),
  },
  {
    name: "Vuex/Pinia",
    icon: "💾",
    category: "前端核心",
    description: "状态管理解决方案",
    image: getImage("pinia.svg"),
  },
  {
    name: "uni-app",
    icon: "📱",
    category: "前端核心",
    description: "App、小程序、H5多端统一开发",
    image: getImage("uni-app.svg"),
  },
  {
    name: "Nuxt4",
    icon: "⚡",
    category: "前端核心",
    description: "服务端渲染(SSR)/静态站点生成(SSG)",
    image: getImage("Nuxt.svg"),
  },
  { name: "Less/Sass", icon: "🎨", category: "前端核心", description: "CSS预处理器" },

  // 后台管理系统
  {
    name: "Element Plus",
    icon: "📦",
    category: "组件库",
    description: "Vue 3组件库",
    image: getImage("element-plus.svg"),
  },
  {
    name: "Element UI",
    icon: "📦",
    category: "组件库",
    description: "Vue 2组件库",
    image: getImage("element-plus.svg"),
  },
  {
    name: "Ant Design Vue",
    icon: "🐜",
    category: "组件库",
    description: "企业级UI组件库",
    image: getImage("Ant Design Vue.svg"),
  },
  { name: "ECharts", icon: "📊", category: "数据可视化", description: "数据图表展示", image: getImage("ECharts.svg") },
  { name: "AntV", icon: "📈", category: "数据可视化", description: "数据可视化解决方案", image: getImage("antv.svg") },

  // 工程化与工具
  { name: "Vite", icon: "⚡", category: "工程化", description: "构建工具配置与优化", image: getImage("vite.svg") },
  { name: "Webpack", icon: "📦", category: "工程化", description: "模块打包工具", image: getImage("Webpack.svg") },
  { name: "ESLint", icon: "✏️", category: "工程化", description: "代码质量检查", image: getImage("eslint.svg") },
  { name: "Prettier", icon: "💅", category: "工程化", description: "代码格式化", image: getImage("prettier.svg") },
  {
    name: "StyleLint",
    icon: "🎨",
    category: "工程化",
    description: "CSS代码质量检查",
    image: getImage("stylelint.svg"),
  },
  {
    name: "Node.js",
    icon: "🟢",
    category: "后端",
    description: "服务端开发，脚本编写",
    image: getImage("Node.js.svg"),
  },
  { name: "Express", icon: "🚀", category: "后端", description: "Node.js Web框架", image: getImage("Express.svg") },
  { name: "SQLite", icon: "🗃️", category: "后端", description: "轻量级数据库", image: getImage("sqlite.svg") },
  { name: "Git", icon: "📦", category: "工具", description: "代码管理与分支管理", image: getImage("git.svg") },
  {
    name: "VS Code插件开发",
    icon: "💻",
    category: "工具",
    description: "编辑器插件开发",
    image: getImage("VS Code.svg"),
  },

  // 高级技术
  { name: "Three.js", icon: "🎭", category: "3D", description: "3D场景开发", image: getImage("Three.js.svg") },
  { name: "Cesium", icon: "🌍", category: "3D", description: "3D地球可视化", image: getImage("cesium.svg") },
  { name: "WebSocket", icon: "🔄", category: "网络", description: "实时通信", image: getImage("websocket.svg") },
  { name: "vue-i18n", icon: "🌐", category: "国际化", description: "多语言支持", image: getImage("vue-i18n.svg") },
  { name: "Guacamole", icon: "🖥️", category: "高级技术", description: "Web远程桌面连接" },
  { name: "xterm.js", icon: "💻", category: "高级技术", description: "Web终端" },
  { name: "vis.js", icon: "📊", category: "高级技术", description: "网络拓扑可视化", image: getImage("vis.svg") },

  // AI 集成与网络
  {
    name: "SSE",
    icon: "📡",
    category: "AI集成",
    description: "Server-Sent Events流式传输",
    image: getImage("SSE.svg"),
  },
  { name: "Ollama", icon: "🤖", category: "AI集成", description: "本地大语言模型服务", image: getImage("Ollama.svg") },
  { name: "Trae", icon: "🤖", category: "AI集成", description: "AI编程工具", image: getImage("trae.svg") },
];

// 经历数据
const experiences = [
  {
    title: "前端开发工程师",
    company: "北京安天网络安全技术有限公司成都分公司",
    period: "2021.10-2026.03",
    description:
      "1.主导前端开发：负责网络安全实训靶场前端系统的整体设计与开发，采用 Monorepo 架构统一管理多个前端项目，带领 1-3 人团队协作完成项目，确保项目按时交付；主导多仓库整合与架构重构，提升代码复用率与团队协作效率。2.技术栈选型与架构设计：根据项目需求和技术发展趋势，选择 Vue 3、TypeScript、Vite/Vue CLI 、Turbo、Playwright等主流技术栈，设计高内聚低耦合的系统架构，保障各子系统高效协作。3.前端基建与工程化：搭建前端工程化体系，包括代码规范（ESLint、Prettier、Stylelint）、构建流程、部署策略等；抽离 Vue 后台管理系统脚手架，支持 vue-cli 和 vite 两个版本，为不同项目提供标准化的开发环境。4.组件库与文档建设：构建共享组件库，开发组件库文档，实现组件的复用和标准化，提升开发效率和代码质量。5.配置管理与自动化：将项目配置抽离为统一管理，实现配置的集中化和复用；开发 Node 脚本实现自动化构建、部署和 Git 子树管理，减少手动操作，提高工作效率。6.性能优化与技术创新：通过代码分割、Tree Shaking、按需加载等优化策略减小打包体积，实现组件按需加载、路由懒加载，提升页面加载速度 40%；深度定制 Guacamole 源代码，解决 Web 远程桌面连接稳定性问题。7.团队协作与指导：指导团队成员进行代码开发，解决技术难题，促进团队技术能力提升，实现多仓库整合与 Monorepo 架构落地。",
  },
  {
    title: "前端开发工程师",
    company: "邦道科技有限公司",
    period: "2019.10-2021.10",
    description:
      "- 负责公司前端项目的技术选型、架构设计和核心功能实现，主导开发多个公司业务相关的前端项目。- 搭建项目基础架构，配置开发环境和构建流程，确保项目开发的高效性和一致性。- 封装通用组件和工具函数，提高代码复用率和开发效率，优化项目性能和用户体验。- 解决项目中的技术难点和性能问题，确保项目顺利上线和稳定运行。- 指导和协助 1-3 名开发人员完成项目开发工作，提升团队整体技术水平和协作能力。",
  },
  {
    title: "前端开发工程师",
    company: "成都天人地网络科技有限公司",
    period: "2019.03-2019.10",
    description:
      "1.负责公司前端项目的设计、开发和维护2.参与产品需求分析和技术方案设计3.与后端开发团队协作，实现前后端数据交互4.优化前端性能，提升用户体验5.维护和更新公司官网及相关业务系统",
  },
  {
    title: "前端开发工程师",
    company: "四川驰诺科技有限公司",
    period: "2018.06-2018.12",
    description: `1.负责拍个全景AR平台全端开发与迭代工作，基于PSD设计稿完成页面切片、排版布局及动态效果实现；
    2.使用HTML5/CSS3、jQuery、Vue-CLI开发平台系统、移动端官网及小程序，独立完成页面搭建与交互功能开发；
    3.对接后端数据接口实现前后端数据交互，结合ECharts、Bootstrap、PHP、MySQL完成转盘抽奖、微投票等营销插件的功能开发与数据落地；
    4.保障页面兼容性、交互流畅度及功能稳定性，支撑平台实景认证、营销互动等核心业务落地。`,
  },
];

// 统计数据
const stats = [
  { value: "8+", label: "年经验" },
  { value: "30+", label: "项目完成" },
  { value: "25+", label: "技术栈" },
];

// 联系项数据
const contactItems = [
  { icon: "📧", label: "邮箱", value: "2510902754@qq.com", link: "mailto:2510902754@qq.com" },
  { icon: "📱", label: "电话", value: "+86 147 0800 9591" },
  { icon: "📍", label: "位置", value: "四川 · 成都" },
];

// 导航栏选中状态
const activeNav = ref("home");

const updateActiveNav = () => {
  const currentPath = window.location.hash || "#home";
  const path = currentPath.replace("#", "");
  activeNav.value = path || "home";
};

onMounted(() => {
  updateActiveNav();
  window.addEventListener("hashchange", updateActiveNav);
});

// 项目分类筛选
const categories = computed(() => {
  const uniqueCategories = new Set(projects.map((project) => project.category));
  return ["全部", ...Array.from(uniqueCategories)];
});

// 打字效果
const heroTitle = ref("");
const heroDescription = ref("");
const aboutTexts = ref([]);
const isTypingHero = ref(false);
const isTypingAbout = ref(false);

const fullHeroTitle = "杜小梅";
const fullHeroDescription =
  "你好！我有 8 年前端开发经验，专注ToB 企业级后台管理系统，具备H5、数据可视化、3D 可视化、uni-app及小程序开发能力，主导过架构设计、Monorepo 改造、组件库建设与 CI/CD流水线落地，可独立完成技术选型、性能优化与团队管理；掌握芋道（Yudao）低代码平台二次开发，实现业务模块快速落地。";

const fullAboutTexts = [
  "我拥有 8 年前端开发经验，专注企业级后台管理系统，具备前端架构设计、工程化建设与团队管理能力。",
  "主导企业级项目全生命周期开发，完成 Monorepo 改造、模块化与组件化建设，制定代码规范与 Git 工作流，基于 Jenkins 搭建 CI/CD 流水线，提升团队协作效率与代码质量。",
  "可独立完成技术选型、核心模块开发、性能优化与团队技术指导，覆盖 3D 可视化、实时通信、AI集成等复杂业务场景落地。",
  "补充自学实践：拓展跨端开发能力，基于 uni-app 独立完成 App、小程序、H5 多端一体化开发与适配；深入研究 Nuxt4 框架并完成存量项目重构，结合 Node.js、Express、SQLite 实现前后端全栈开发落地；基于芋道（Yudao）低代码平台完成二次开发：搭建本地前后端环境，通过 Vue3 管理后台定制业务菜单、配置生成参数，编写 SQL 脚本并完成代码包生成；将前端组件、后端代码及数据库脚本集成至项目，验证全链路功能正常，实现业务菜单模块快速落地。",
  "工具链创新：在日常开发中深度集成 AI编程工具（Trae），用于自动化文档生成、代码片段生成、接口注释完善及基础逻辑编写，提升需求拆解与文档维护效率。",
];

// 打字效果函数
const typeWriter = (text, refVar, speed = 50) => {
  return new Promise((resolve) => {
    let index = 0;
    refVar.value = "";
    const timer = setInterval(() => {
      if (index < text.length) {
        refVar.value += text.charAt(index);
        index++;
      } else {
        clearInterval(timer);
        resolve();
      }
    }, speed);
  });
};

// 多行打字效果
const typeWriterMultiple = (texts, refArray, speed = 30) => {
  return new Promise(async (resolve) => {
    refArray.value = [];
    for (let i = 0; i < texts.length; i++) {
      refArray.value.push("");
      await typeWriterToArray(texts[i], refArray, i, speed);
    }
    resolve();
  });
};

const typeWriterToArray = (text, refArray, index, speed) => {
  return new Promise((resolve) => {
    let charIndex = 0;
    const timer = setInterval(() => {
      if (charIndex < text.length) {
        refArray.value[index] += text.charAt(charIndex);
        charIndex++;
        // 触发响应式更新
        refArray.value = [...refArray.value];
      } else {
        clearInterval(timer);
        resolve();
      }
    }, speed);
  });
};

// 页面加载时启动打字效果
onMounted(async () => {
  // Hero 部分打字效果
  isTypingHero.value = true;
  await typeWriter(fullHeroDescription, heroDescription, 80);
  isTypingHero.value = false;

  // 延迟后启动 About 部分打字效果
  setTimeout(async () => {
    isTypingAbout.value = true;
    await typeWriterMultiple(fullAboutTexts, aboutTexts, 20);
    isTypingAbout.value = false;
  }, 1000);

  // 滚动触发动画
  const observerOptions = {
    threshold: 0.1,
    rootMargin: "-50px 0px -50px 0px",
  };

  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        // 为不同类型的元素添加不同的动画
        const element = entry.target;

        if (element.classList.contains("section-title")) {
          element.classList.add("animate__animated", "animate__fadeInUp");
        } else if (element.classList.contains("section-subtitle")) {
          element.classList.add("animate__animated", "animate__fadeInUp", "animate__delay-1s");
        } else if (element.classList.contains("experience-item")) {
          element.classList.add("animate__animated", "animate__fadeInLeft");
        } else if (element.classList.contains("skill-card")) {
          element.classList.add("animate__animated", "animate__fadeInUp");
        } else if (element.classList.contains("project-item")) {
          element.classList.add("animate__animated", "animate__fadeInUp");
        } else if (element.classList.contains("contact-item")) {
          element.classList.add("animate__animated", "animate__fadeInUp");
        } else if (element.classList.contains("stat-card")) {
          element.classList.add("animate__animated", "animate__fadeInUp");
        } else if (element.classList.contains("about-left")) {
          element.classList.add("animate__animated", "animate__fadeInLeft");
        } else if (element.classList.contains("about-right")) {
          element.classList.add("animate__animated", "animate__fadeInRight");
        }

        // 停止观察已触发动画的元素
        observer.unobserve(element);
      }
    });
  }, observerOptions);

  // 观察所有需要滚动触发动画的元素
  document.querySelectorAll(".animate-on-scroll").forEach((element) => {
    observer.observe(element);
  });
});

const selectedCategory = ref("全部");

const filteredProjects = computed(() => {
  if (selectedCategory.value === "全部") {
    return projects;
  }
  return projects.filter((project) => project.category === selectedCategory.value);
});

// 项目详情页
const selectedProject = ref(null);

const openProjectDetails = (project) => {
  console.log("🚀 ~ openProjectDetails ~ project:", project);
  selectedProject.value = project;
};

const closeProjectDetails = () => {
  selectedProject.value = null;
};

// 图片查看器
const selectedImage = ref(null);

const openImageViewer = (image) => {
  selectedImage.value = image;
  document.body.style.overflow = "hidden";
};

const closeImageViewer = () => {
  selectedImage.value = null;
  document.body.style.overflow = "";
};
</script>

<template>
  <div class="app">
    <!-- Navigation -->
    <nav class="navbar animate__animated animate__fadeInDown animate__delay-1s">
      <div class="container nav-container">
        <div class="logo">
          <div class="logo-icon"><img src="./assets/logo.svg" alt="" /></div>
          <div>
            <div class="logo-text">杜小梅</div>
            <div class="logo-desc">前端开发工程师</div>
          </div>
        </div>
        <div class="nav-links">
          <a
            href="#"
            :class="{ 'nav-cta': activeNav === 'home' }"
            class="animate__animated animate__fadeIn animate__delay-2s"
            >首页</a
          >
          <a
            href="#about"
            :class="{ 'nav-cta': activeNav === 'about' }"
            class="animate__animated animate__fadeIn animate__delay-2-1s"
            >关于</a
          >
          <a
            href="#experience"
            :class="{ 'nav-cta': activeNav === 'experience' }"
            class="animate__animated animate__fadeIn animate__delay-2-2s"
            >经验</a
          >
          <a
            href="#skills"
            :class="{ 'nav-cta': activeNav === 'skills' }"
            class="animate__animated animate__fadeIn animate__delay-2-3s"
            >技能</a
          >
          <a
            href="#projects"
            :class="{ 'nav-cta': activeNav === 'projects' }"
            class="animate__animated animate__fadeIn animate__delay-2-4s"
            >项目</a
          >
          <a
            href="#contact"
            :class="{ 'nav-cta': activeNav === 'contact' }"
            class="animate__animated animate__fadeIn animate__delay-2-5s"
            >联系</a
          >
        </div>
      </div>
    </nav>

    <!-- Hero Section -->
    <section class="hero">
      <div class="hero-bg">
        <div class="gradient-orb orb-1 animate__animated animate__zoomIn animate__delay-1s"></div>
        <div class="gradient-orb orb-2 animate__animated animate__zoomIn animate__delay-1-3s"></div>
        <div class="gradient-orb orb-3 animate__animated animate__zoomIn animate__delay-1-6s"></div>
      </div>
      <div class="container">
        <div class="hero-content animate__animated animate__fadeInUp animate__delay-1-5s">
          <div class="hero-badge">
            <span class="badge-dot"></span>
            前端开发者 & 技术小组长
          </div>
          <h1 class="hero-title">
            杜小梅<br />
            <span class="gradient-text">前端开发工程师</span>
          </h1>
          <p class="hero-description">
            <span v-if="isTypingHero" class="typing-text"
              >{{ heroDescription }}<span class="typing-cursor">|</span></span
            >
            <span v-else>{{ heroDescription }}</span>
          </p>
          <div class="hero-actions">
            <a href="#projects" class="btn-primary animate__animated animate__fadeInUp animate__delay-2-5s">
              <span>查看项目</span>
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M5 12h14M12 5l7 7-7 7" />
              </svg>
            </a>
            <a href="#contact" class="btn-secondary animate__animated animate__fadeInUp animate__delay-2-7s">联系我</a>
          </div>
          <div class="social-links">
            <a
              href="https://github.com/plum-blossom"
              class="social-link animate__animated animate__bounceIn animate__delay-3s"
              title="GitHub"
            >
              <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor">
                <path
                  d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
                />
              </svg>
            </a>
            <a
              href="https://gitee.com/plumbloosom"
              class="social-link animate__animated animate__bounceIn animate__delay-3-1s"
              title="Gitee"
            >
              <svg
                t="1775209578055"
                class="icon"
                viewBox="0 0 1024 1024"
                version="1.1"
                xmlns="http://www.w3.org/2000/svg"
                p-id="2393"
                width="24"
                height="200"
              >
                <path
                  d="M512 1024C229.2224 1024 0 794.7776 0 512S229.2224 0 512 0s512 229.2224 512 512-229.2224 512-512 512z m259.1488-568.8832H480.4096a25.2928 25.2928 0 0 0-25.2928 25.2928l-0.0256 63.2064c0 13.952 11.3152 25.2928 25.2672 25.2928h177.024c13.9776 0 25.2928 11.3152 25.2928 25.2672v12.6464a75.8528 75.8528 0 0 1-75.8528 75.8528H366.592a25.2928 25.2928 0 0 1-25.2672-25.2928v-240.1792a75.8528 75.8528 0 0 1 75.8272-75.8528h353.9456a25.2928 25.2928 0 0 0 25.2672-25.2928l0.0768-63.2064a25.2928 25.2928 0 0 0-25.2672-25.2928H417.152a189.6192 189.6192 0 0 0-189.6192 189.6448v353.9456c0 13.9776 11.3152 25.2928 25.2928 25.2928h372.9408a170.6496 170.6496 0 0 0 170.6496-170.6496v-145.408a25.2928 25.2928 0 0 0-25.2928-25.2672z"
                  fill="#C71D23"
                  p-id="2394"
                ></path>
              </svg>
            </a>
          </div>
        </div>
      </div>
    </section>

    <!-- About Section -->
    <section id="about" class="about">
      <div class="container">
        <h2 class="section-title animate-on-scroll">关于我</h2>
        <p class="section-subtitle animate-on-scroll">了解代码背后的人</p>
        <div class="about-grid">
          <div class="about-image-wrapper animate-on-scroll about-left">
            <div class="about-image">
              <img src="./assets/蓝底寸照.jpg" alt="杜小梅" />
              <div class="image-glow"></div>
            </div>
          </div>
          <div class="about-content animate-on-scroll about-right">
            <div class="about-text">
              <p v-for="(text, index) in isTypingAbout ? aboutTexts : fullAboutTexts" :key="index">
                <span v-if="isTypingAbout && index === aboutTexts.length - 1" class="typing-text">
                  {{ text }}<span class="typing-cursor">|</span>
                </span>
                <span v-else>{{ text }}</span>
              </p>
            </div>
            <div class="stats-grid">
              <div v-for="(stat, index) in stats" :key="index" class="stat-card animate-on-scroll">
                <div class="stat-value">{{ stat.value }}</div>
                <div class="stat-label">{{ stat.label }}</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Experience Section -->
    <section id="experience" class="experience">
      <div class="container">
        <h2 class="section-title animate-on-scroll">工作经历</h2>
        <p class="section-subtitle animate-on-scroll">我的专业旅程与职业成长</p>
        <div class="experience-list">
          <div v-for="(exp, index) in experiences" :key="index" class="experience-item glass-card animate-on-scroll">
            <div class="experience-header">
              <div class="experience-title-group">
                <h3 class="experience-title">{{ exp.title }}</h3>
                <span class="experience-company">{{ exp.company }}</span>
              </div>
              <span class="experience-period">{{ exp.period }}</span>
            </div>
            <p class="experience-description">{{ exp.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="skills">
      <div class="container">
        <h2 class="section-title animate-on-scroll">技能与技术</h2>
        <p class="section-subtitle animate-on-scroll">将创意变为现实的神奇工具</p>
        <div class="skills-grid">
          <div v-for="(skill, index) in skills" :key="index" class="skill-card glass-card animate-on-scroll">
            <div class="skill-icon">
              <img v-if="skill.image" :src="skill.image" :alt="skill.name" class="skill-image" />
              <span v-else>{{ skill.icon }}</span>
            </div>
            <div class="skill-name">{{ skill.name }}</div>
            <div class="skill-category">{{ skill.category }}</div>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="projects">
      <div class="container">
        <h2 class="section-title animate-on-scroll">精选项目</h2>
        <p class="section-subtitle animate-on-scroll">我的创意作品与技术专长展示</p>
        <!-- 项目分类筛选 -->
        <div class="project-filters">
          <button
            v-for="(category, index) in categories"
            :key="category"
            :class="{ active: selectedCategory === category }"
            @click="selectedCategory = category"
            class="filter-btn animate-on-scroll"
          >
            {{ category }}
          </button>
        </div>
        <div class="projects-grid">
          <div
            v-for="(project, index) in filteredProjects"
            :key="project.id"
            @click="openProjectDetails(project)"
            class="project-item animate-on-scroll"
          >
            <ProjectCard
              :title="project.title"
              :description="project.description"
              :image="project.image"
              :tags="project.tags"
              :link="project.link"
              :companyProject="project.companyProject"
              :demoLinks="project.demoLinks"
            />
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="contact">
      <div class="container">
        <h2 class="section-title animate-on-scroll">联系我</h2>
        <p class="section-subtitle animate-on-scroll">无论是项目合作、技术交流还是工作机会，都欢迎与我联系。</p>
        <div class="contact-info">
          <div class="contact-items">
            <div v-for="(item, index) in contactItems" :key="index" class="contact-item animate-on-scroll">
              <div class="contact-icon">{{ item.icon }}</div>
              <div class="contact-detail">
                <span class="contact-label">{{ item.label }}</span>
                <a v-if="item.link" :href="item.link">{{ item.value }}</a>
                <span v-else>{{ item.value }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
      <div class="container">
        <div class="footer-bottom">
          <p>&copy; 2026 个人作品集. 保留所有权利.</p>
        </div>
      </div>
    </footer>

    <!-- 项目详情模态框 -->
    <div
      v-if="selectedProject"
      class="project-modal animate__animated animate__fadeIn"
      @click.self="closeProjectDetails"
    >
      <div class="project-modal-content animate__animated animate__zoomIn">
        <button class="close-btn" @click="closeProjectDetails">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <line x1="18" y1="6" x2="6" y2="18"></line>
            <line x1="6" y1="6" x2="18" y2="18"></line>
          </svg>
        </button>
        <div class="project-modal-header">
          <h2>{{ selectedProject.title }}</h2>
          <div class="project-info">
            <span class="project-period">{{ selectedProject.period }}</span>
            <span class="project-category">{{ selectedProject.category }}</span>
          </div>
          <div class="project-tags">
            <span v-for="(tag, index) in selectedProject.tags" :key="index" class="tag">{{ tag }}</span>
          </div>
        </div>
        <div class="project-modal-body">
          <div class="project-images">
            <div
              v-for="(img, index) in selectedProject.images"
              title="点击查看大图"
              :key="index"
              class="project-image-item"
            >
              <img
                :src="img"
                :alt="selectedProject.title + ' ' + (index + 1)"
                @click="openImageViewer(img)"
                style="cursor: pointer"
                :class="selectedProject?.imageClass ? selectedProject.imageClass : ''"
              />
            </div>
          </div>
          <div class="project-description">
            <h3>项目描述</h3>
            <p>{{ selectedProject.description }}</p>

            <h3>项目周期</h3>
            <p>{{ selectedProject.period }}</p>

            <h3>技术栈</h3>
            <ul>
              <li v-for="(tag, index) in selectedProject.tags" :key="index">{{ tag }}</li>
            </ul>

            <h3>项目职责</h3>
            <ul v-if="selectedProject.responsibilities">
              <li v-for="(responsibility, index) in selectedProject.responsibilities" :key="index">
                {{ responsibility }}
              </li>
            </ul>
            <p v-else>负责项目的前端开发，包括需求分析、技术选型、架构设计、代码实现和性能优化等工作。</p>

            <h3 v-if="selectedProject.achievements">项目成果</h3>
            <ul v-if="selectedProject.achievements">
              <li v-for="(achievement, index) in selectedProject.achievements" :key="index">{{ achievement }}</li>
            </ul>

            <!-- 个人学习项目资源 -->
            <div v-if="selectedProject.demoLinks" class="project-demo-resources">
              <h3>项目资源</h3>
              <div v-for="(demo, index) in selectedProject.demoLinks" :key="index" class="demo-resource-item">
                <h4>{{ demo.name }}</h4>
                <div class="demo-links">
                  <a v-if="demo.sourceCode" :href="demo.sourceCode" target="_blank" class="demo-link source-code">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                      <path
                        d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"
                      ></path>
                    </svg>
                    源码仓库
                  </a>
                  <a v-if="demo.demoLink" :href="demo.demoLink" target="_blank" class="demo-link demo-site">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                      <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6M15 3h6v6M10 14L21 3" />
                    </svg>
                    在线演示
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="project-modal-footer">
          <button class="btn-secondary" @click="closeProjectDetails">返回</button>
        </div>
      </div>
    </div>

    <!-- 图片查看器模态框 -->
    <div
      v-if="selectedImage"
      class="image-viewer-modal animate__animated animate__fadeIn"
      @click.self="closeImageViewer"
    >
      <div class="image-viewer-content animate__animated animate__zoomIn">
        <button class="close-btn" @click="closeImageViewer">
          <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <line x1="18" y1="6" x2="6" y2="18"></line>
            <line x1="6" y1="6" x2="18" y2="18"></line>
          </svg>
        </button>
        <div class="image-viewer-body">
          <img :src="selectedImage" :alt="'放大图片'" />
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.app {
  min-height: 100vh;
  background: var(--bg-primary);
}

/* Navigation */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 1rem 0;
  background: rgba(10, 10, 15, 0.8);
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--border-color);
}

.nav-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  display: flex;
  align-items: center;
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text-primary);
}

.logo-icon {
  font-size: 1.5rem;
  margin-right: 0.5rem;
  width: 48px;
  height: 48px;
}

.logo-text {
  display: block;
  background: linear-gradient(135deg, var(--text-primary) 0%, var(--purple-light) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.logo-desc {
  font-size: 0.7rem;
  font-weight: 400;
  color: var(--text-secondary);
  display: block;
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.nav-links a {
  color: var(--text-secondary);
  font-size: 0.95rem;
  transition: color 0.3s ease;
}

.nav-links a:hover {
  color: var(--text-primary);
}

.nav-cta {
  background: linear-gradient(135deg, var(--purple-primary) 0%, var(--purple-secondary) 100%);
  color: white !important;
  padding: 0.6rem 1.2rem;
  border-radius: 50px;
  font-weight: 600;
}

.nav-cta:hover {
  box-shadow: 0 4px 15px rgba(168, 85, 247, 0.4);
}

/* 项目卡片点击效果 */
.project-item {
  cursor: pointer;
  transition: transform 0.3s ease;
}

.project-item:hover {
  transform: translateY(-5px);
}

/* 项目详情模态框 */
.project-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(10, 10, 15, 0.95);
  backdrop-filter: blur(20px);
  z-index: 2000;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
}

.project-modal-content {
  background: var(--bg-secondary);
  border: 1px solid var(--border-color);
  border-radius: 20px;
  padding: 2.5rem;
  max-width: 900px;
  max-height: 80vh;
  overflow-y: auto;
  position: relative;
  box-shadow: 0 20px 60px rgba(168, 85, 247, 0.2);
}

.close-btn {
  position: absolute;
  top: 1.5rem;
  right: 1.5rem;
  background: var(--bg-glass);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--text-secondary);
  cursor: pointer;
  transition: all 0.3s ease;
}

.close-btn:hover {
  background: var(--bg-card);
  border-color: var(--purple-primary);
  color: var(--purple-light);
}

.project-modal-header {
  margin-bottom: 2rem;
}

.project-modal-header h2 {
  font-size: 2rem;
  margin-bottom: 1rem;
  background: linear-gradient(135deg, var(--text-primary) 0%, var(--purple-light) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.project-info {
  display: flex;
  gap: 1rem;
  margin-bottom: 1rem;
  flex-wrap: wrap;
}

.project-period {
  background: var(--bg-glass);
  border: 1px solid var(--border-color);
  border-radius: 50px;
  padding: 0.25rem 0.75rem;
  font-size: 0.85rem;
  color: var(--text-secondary);
  font-family: var(--font-mono);
}

.project-category {
  background: var(--bg-glass);
  border: 1px solid var(--border-color);
  border-radius: 50px;
  padding: 0.25rem 0.75rem;
  font-size: 0.85rem;
  color: var(--text-secondary);
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.project-tags .tag {
  background: var(--bg-glass);
  border: 1px solid var(--border-color);
  border-radius: 50px;
  padding: 0.25rem 0.75rem;
  font-size: 0.85rem;
  color: var(--text-secondary);
}

.project-modal-body {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2rem;
  margin-bottom: 2rem;
}

.project-image {
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(168, 85, 247, 0.2);
}

.project-image img {
  width: 100%;
  aspect-ratio: 16/9;
  object-fit: cover;
}

.project-images {
  margin-bottom: 2rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.project-image-item {
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(168, 85, 247, 0.2);
}

.project-image-item img {
  width: 100%;
  aspect-ratio: 16/9;
  object-fit: cover;
}
.project-image-item img.ara {
  aspect-ratio: auto;
}

@media (max-width: 768px) {
  .project-images {
    grid-template-columns: 1fr;
  }
}

/* 图片查看器模态框 */
.image-viewer-modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.95);
  backdrop-filter: blur(20px);
  z-index: 3000;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
}

.image-viewer-content {
  position: relative;
  max-width: 90%;
  max-height: 90vh;
  overflow: hidden;
}

.image-viewer-body {
  display: flex;
  align-items: center;
  justify-content: center;
}

.image-viewer-body img {
  max-width: 100%;
  max-height: 80vh;
  object-fit: contain;
  border-radius: 8px;
}

@media (max-width: 768px) {
  .image-viewer-modal {
    padding: 1rem;
  }

  .image-viewer-content {
    max-width: 95%;
  }

  .image-viewer-body img {
    max-height: 70vh;
  }
}

.project-description h3 {
  font-size: 1.25rem;
  margin-bottom: 0.75rem;
  color: var(--text-primary);
}

.project-description p {
  margin-bottom: 1.5rem;
  color: var(--text-secondary);
}

.project-description ul {
  margin-bottom: 1.5rem;
  padding-left: 1.5rem;
}

.project-description li {
  color: var(--text-secondary);
  margin-bottom: 0.5rem;
}

.project-modal-footer {
  display: flex;
  gap: 1rem;
  justify-content: flex-end;
}

@media (max-width: 768px) {
  .project-modal {
    padding: 1rem;
  }

  .project-modal-content {
    padding: 1.5rem;
    max-height: 90vh;
  }

  .project-modal-body {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .project-modal-footer {
    flex-direction: column;
  }

  .project-modal-footer button,
  .project-modal-footer a {
    width: 100%;
  }
}

/* Hero Section */
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  position: relative;
  overflow: hidden;
  padding-top: 80px;
}

.hero-bg {
  position: absolute;
  inset: 0;
  z-index: 0;
}

.gradient-orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(80px);
  opacity: 0.5;
}

.orb-1 {
  width: 600px;
  height: 600px;
  background: linear-gradient(135deg, var(--purple-primary), var(--purple-secondary));
  top: -200px;
  right: -100px;
}

.orb-2 {
  width: 400px;
  height: 400px;
  background: linear-gradient(135deg, var(--accent-pink), var(--purple-primary));
  bottom: -100px;
  left: -100px;
}

.orb-3 {
  width: 300px;
  height: 300px;
  background: linear-gradient(135deg, var(--accent-blue), var(--purple-secondary));
  top: 50%;
  left: 30%;
  opacity: 0.3;
}

.hero-content {
  position: relative;
  z-index: 1;
  max-width: 800px;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem 1rem;
  background: var(--bg-glass);
  border: 1px solid var(--border-color);
  border-radius: 50px;
  font-size: 0.9rem;
  color: var(--text-secondary);
  margin-bottom: 1.5rem;
}

.badge-dot {
  width: 8px;
  height: 8px;
  background: #22c55e;
  border-radius: 50%;
  animation: pulse 2s infinite;
}

@keyframes pulse {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

.hero-title {
  font-size: 4rem;
  font-weight: 800;
  line-height: 1.1;
  margin-bottom: 1.5rem;
}

.hero-description {
  font-size: 1.25rem;
  color: var(--text-secondary);
  max-width: 600px;
  margin-bottom: 2rem;
}

.hero-actions {
  display: flex;
  gap: 1rem;
  margin-bottom: 3rem;
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  width: 48px;
  height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--bg-glass);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  color: var(--text-secondary);
  transition: all 0.3s ease;
}

.social-link:hover {
  background: var(--bg-card);
  border-color: var(--purple-primary);
  color: var(--purple-light);
  transform: translateY(-3px);
}

/* About Section */
.about {
  padding: 8rem 0;
  background: var(--bg-secondary);
}

.about-grid {
  display: grid;
  grid-template-columns: 1fr 1.5fr;
  gap: 4rem;
  align-items: center;
}

.about-image-wrapper {
  position: relative;
}

.about-image {
  position: relative;
  border-radius: 20px;
  overflow: hidden;
}

.about-image img {
  width: 100%;
  aspect-ratio: 3/4;
  object-fit: cover;
}

.image-glow {
  position: absolute;
  inset: -20px;
  background: linear-gradient(135deg, var(--purple-primary), var(--accent-pink));
  border-radius: 30px;
  opacity: 0.3;
  filter: blur(40px);
  z-index: -1;
}

.about-content {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.about-text p {
  font-size: 1.1rem;
  margin-bottom: 1rem;
}

.stats-grid {
  display: flex;
  gap: 2rem;
}

.stat-card {
  background: var(--bg-card);
  backdrop-filter: blur(20px);
  border: 1px solid var(--border-color);
  border-radius: 16px;
  padding: 1.5rem 2rem;
  text-align: center;
  transition: all 0.3s ease;
}

.stat-card:hover {
  border-color: var(--border-glow);
  transform: translateY(-5px);
}

.stat-value {
  font-size: 2.5rem;
  font-weight: 800;
  background: linear-gradient(135deg, var(--purple-light), var(--accent-pink));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.stat-label {
  color: var(--text-muted);
  font-size: 0.9rem;
}

/* Experience Section */
.experience {
  padding: 8rem 0;
  background: var(--bg-primary);
}

.experience-list {
  max-width: 800px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.experience-item {
  padding: 2rem;
}

.experience-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  margin-bottom: 1rem;
}

.experience-title {
  font-size: 1.25rem;
  margin-bottom: 0.25rem;
}

.experience-company {
  color: var(--purple-light);
  font-size: 0.95rem;
}

.experience-period {
  color: var(--text-muted);
  font-size: 0.9rem;
  font-family: var(--font-mono);
}

.experience-description {
  color: var(--text-secondary);
  margin: 0;
}

/* Skills Section */
.skills {
  padding: 8rem 0;
  background: var(--bg-secondary);
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: 1.5rem;
  max-width: 900px;
  margin: 0 auto;
}

.skill-card {
  padding: 1.5rem;
  text-align: center;
}

.skill-icon {
  font-size: 2.5rem;
  margin-bottom: 0.75rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.skill-image {
  width: 48px;
  height: 48px;
  object-fit: contain;
}

.skill-name {
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.25rem;
}

.skill-category {
  font-size: 0.8rem;
  color: var(--text-muted);
}

/* Projects Section */
.projects {
  padding: 8rem 0;
  background: var(--bg-primary);
}

.project-filters {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  margin-bottom: 3rem;
  justify-content: center;
}

.filter-btn {
  background: var(--bg-glass);
  border: 1px solid var(--border-color);
  border-radius: 50px;
  padding: 0.75rem 1.5rem;
  color: var(--text-secondary);
  font-size: 0.9rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.filter-btn:hover {
  background: var(--bg-card);
  border-color: var(--purple-primary);
  color: var(--purple-light);
}

.filter-btn.active {
  background: linear-gradient(135deg, var(--purple-primary) 0%, var(--purple-secondary) 100%);
  color: white;
  border-color: var(--purple-primary);
  box-shadow: 0 4px 15px rgba(168, 85, 247, 0.4);
}

.projects-grid {
  column-count: 3;
  column-gap: 2rem;
  break-inside: avoid;
}

/* 响应式瀑布流布局 */
@media (max-width: 1200px) {
  .projects-grid {
    column-count: 2;
  }
}

@media (max-width: 768px) {
  .projects-grid {
    column-count: 1;
  }
}

/* 防止项目卡片被分割到不同列 */
.project-item {
  break-inside: avoid;
  margin-bottom: 2rem;
  display: inline-block;
  width: 100%;
}

/* Contact Section */
.contact {
  padding: 8rem 0;
  background: var(--bg-secondary);
}

.contact-info {
  max-width: 600px;
  margin: 0 auto;
  text-align: center;
}

.contact-info h3 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

.contact-info > p {
  margin-bottom: 2rem;
}

.contact-items {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  align-items: center;
}

.contact-item {
  display: flex;
  align-items: center;
  gap: 1rem;
  width: 100%;
  max-width: 400px;
  text-align: left;
}

.contact-icon {
  width: 48px;
  height: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--bg-card);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  font-size: 1.25rem;
  flex-shrink: 0;
}

.contact-detail {
  display: flex;
  flex-direction: column;
  flex: 1;
}

.contact-label {
  font-size: 0.85rem;
  color: var(--text-muted);
}

.contact-detail a,
.contact-detail span:last-child {
  color: var(--text-primary);
  font-weight: 500;
}

/* Footer */
.footer {
  padding: 3rem 0 2rem;
  background: var(--bg-primary);
}

.footer-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  margin-bottom: 2rem;
}

.footer-brand {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 1.25rem;
  font-weight: 700;
}

.footer-name {
  background: linear-gradient(135deg, var(--text-primary) 0%, var(--purple-light) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.footer-text {
  color: var(--text-muted);
  font-size: 0.9rem;
  margin: 0;
}

.footer-social {
  display: flex;
  gap: 1rem;
}

.footer-bottom {
  text-align: center;
  padding-top: 2rem;
  border-top: 1px solid var(--border-color);
}

.footer-bottom p {
  color: var(--text-muted);
  font-size: 0.9rem;
  margin: 0;
}

/* Responsive Design */
@media (max-width: 968px) {
  .about-grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .about-image-wrapper {
    max-width: 400px;
    margin: 0 auto;
  }

  .contact-grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .hero-title {
    font-size: 3rem;
  }
}

@media (max-width: 768px) {
  .nav-links {
    display: none;
  }

  .hero {
    padding-top: 100px;
  }

  .hero-title {
    font-size: 2.5rem;
  }

  .hero-description {
    font-size: 1.1rem;
  }

  .hero-actions {
    flex-direction: column;
  }

  .stats-grid {
    flex-direction: column;
    gap: 1rem;
  }

  .stat-card {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 1.5rem;
  }

  .experience-header {
    flex-direction: column;
    gap: 0.5rem;
  }

  .project-filters {
    justify-content: flex-start;
    overflow-x: auto;
    padding-bottom: 1rem;
  }

  .filter-btn {
    white-space: nowrap;
  }

  .projects-grid {
    grid-template-columns: 1fr;
  }

  .about,
  .experience,
  .skills,
  .projects,
  .contact {
    padding: 5rem 0;
  }
}
</style>

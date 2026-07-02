# CHANGELOG

## V3.1 — 引擎替换版（2026-07）

### Changed
- 双引擎组合由 MJ7 × NanoBanana2 改为 **ChatGPT Imagen 2 × NanoBanana2**。
- ChatGPT 方言定义为「对话迭代引擎」：首轮结构化场景描述（画幅写进句子、无参数语法）+ 迭代指令（一轮只改一件事、显式声明保持项）；文字渲染强，封面标题可直出；角色一致性用参考图+指令而非参数。
- 新增「两引擎分工建议」：反复精修选 ChatGPT，一次出图/批量分镜选 NB2。
- 同步更新 image_prompt_template、anchor_export_template、全链路示例与引擎级质检清单。


## V3 — 双引擎编译 × 视频模型路由 × 风格锚导出版（2026-07）

### Fixed
- 补上缺失的 YAML frontmatter（name / description / version）——V2 作为 Claude Skill 缺少触发描述，无法被正确路由。

### Added
- **双引擎提示词编译层**：图片提示词默认输出 MJ7（短语化/参数后置/≤3行）+ NanoBanana2（叙述式/自然语句禁止项）两版，与 prism-director-pro 双引擎约定对齐。
- **视频模型路由层**：新增 `data/video_model_router.yaml` 与 `templates/video_prompt_router_template.md`，15s 视频提示词按即梦/Seedance/可灵/Veo/万相分方言输出，继承 video-prompt-craft 三条铁律（长度纪律 30–100 词、一事一提示词、图生视频只写运动+运镜）。
- **风格锚导出层（Mode H）**：新增 `templates/anchor_export_template.md`，任意氛围转译可导出为 prism-style-anchor-framework 标准五维锚卡，含「注入用一句话」。
- 新增 `examples/dual_engine_and_router_example.md` 全链路示例。
- 新增「与其他 Skill 的协作」章节与引擎级质检清单。

### Changed
- `templates/image_prompt_template.md` 升级为双引擎版。
- Mode D/F 重写；Mode G 增加风格锚导出提议。
- 15s 视频输出从"单段英文长文"改为"节拍表+路由建议+模型方言提示词+换模型改法"。


## V2 — 视觉氛围转译版

### Added
- 新增 `data/director_ip_atmosphere.yaml`，作为核心高价值风格库。
- 新增动画 / 艺术 / 视觉氛围的传播版名称与商用安全版转译。
- 新增 `templates/director_ip_translation_template.md`。
- 新增 `examples/director_ip_atmosphere_poster_example.md`。
- 新增 `examples/director_ip_storyboard_example.md`。
- 新增 `examples/prompt_conversion_examples.md`。
- 新增海报资产 `assets/posters/ai-style-atlas-overview.png`。

### Changed
- `SKILL.md` 从通用风格推荐器升级为“氛围转译 + 视觉导演”系统。
- `README.md` 更新为 V2 定位。
- `STYLE_TAXONOMY.md` 改为两层结构：高价值视觉氛围库 + 通用支撑风格库。
- `commercial_safe_aliases.yaml` 增加更多传播名到安全描述的映射。

### Required Core Mappings
- 宫崎骏风格 → 日系手绘治愈动画风
- 皮克斯风格 → 温润家庭向 3D 动画电影感
- 迪士尼风格 → 华丽童话城堡动画感
- 梵高风格 → 后印象派厚涂旋涡笔触
- 莫兰迪风格 → 低饱和灰调静物美学

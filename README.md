# PONYO AI Style Atlas Director Skill

中文名：**AI 艺术风格导演图谱 Skill**  
当前版本：**V3.1.1 — 版权安全转译说明 × 双引擎编译 × 视频模型路由 × 风格锚导出版**

![PONYO AI Style Atlas Director](assets/showcase/00_skill_overview_poster.png)

## 快速入口

- Skill 源码：[`SKILL.md`](SKILL.md)
- 可下载 Skill 包：[`dist/ponyo-ai-style-atlas-director-v3.1.1.skill`](dist/ponyo-ai-style-atlas-director-v3.1.1.skill)
- 风格分类：[`STYLE_TAXONOMY.md`](STYLE_TAXONOMY.md)
- 示例目录：[`examples/`](examples/)

## 下载后怎么用

把 `.skill` 包安装到支持 Skill 的本地 Agent 后，可以直接用下面几句话触发：

```text
用这个题材，帮我推荐 3 个商用安全的视觉氛围。
```

```text
把这个参考风格转成 ChatGPT Image 2 可以直接用的封面提示词。
```

```text
把我的故事扩展成六宫格故事板，并给我 ChatGPT Image 2 版提示词。
```

推荐工作流：

1. **输入用户自己的故事**：可以是一句话梗概、角色设定、文章主题、品牌故事、视频概念或完整脚本。故事板不是凭空生成的，它服务于用户要讲的故事。
2. **补齐故事骨架**：如果用户只给题材，Skill 先补出“主角是谁、想要什么、遇到什么阻碍、发生什么转折、最后停在哪个画面”。
3. **输入或选择参考氛围**：可以说“我想要童话城堡感”“像温暖家庭 3D 动画”“想要低饱和灰调静物气质”，也可以让 Skill 推荐 3 个方向。
4. **先做商用安全转译**：Skill 会把传播版名称转成描述性风格名，例如“华丽童话城堡动画感”“温润家庭向 3D 动画电影感”。
5. **拆视觉 DNA**：输出构图、色彩、光影、材质、镜头、情绪和禁忌。
6. **再选择产物**：可继续生成封面提示词、信息图提示词、六宫格/八宫格故事板、15 秒视频提示词或风格锚卡。
7. **按引擎编译**：图片默认给 ChatGPT Imagen 2 和 NanoBanana2 两版；如果只用 ChatGPT Image 2，就直接要求“只输出 ChatGPT Image 2 版”。

一句话理解：**先讲清用户自己的故事，再把参考感受翻译成安全的视觉语言，最后生成海报、故事板和视频提示词。**

## 版权安全转译机制

这个 Skill 的目标不是“绕过版权审核”，而是**在进入生成模型之前，主动去掉高风险版权元素**，让提示词更像合法的艺术指导，而不是模仿请求。

它的做法是：

1. **传播名只用于沟通，不进入生产提示词**：用户可以说“某某风格”，但最终提示词不写导演名、工作室名、角色名或具体 IP 名。
2. **只保留抽象视觉 DNA**：把参考拆成镜头、构图、色彩、光影、材质、情绪、叙事节奏。
3. **删除可识别专有元素**：不复刻角色脸、服装、Logo、标志道具、经典场景、专属建筑或海报构图。
4. **输出描述性安全标签**：例如把“迪士尼风格”转成“华丽童话城堡动画感”，把“皮克斯风格”转成“温润家庭向 3D 动画电影感”。
5. **保留禁忌清单**：每个方向都写明不要出现什么，避免模型往受保护角色、场景或品牌符号上靠。

示例：

```text
用户说法：想要迪士尼童话风
安全转译：华丽童话城堡动画感
生产提示词：原创梦幻城堡与尖塔剪影，黄金时刻晚霞，湖面倒影，浪漫花园，
精致动画背景，温柔光晕，庄重又梦幻的童话仪式感。
禁忌：不要复制具体城堡、具体公主角色、Logo、过度闪粉、廉价页游梦幻感。
```

换句话说，它不是教你绕开规则，而是帮你把“我想要某种感觉”变成**更安全、更可解释、更可复用**的视觉创作语言。

## 配图展示

| Skill 介绍海报 | 日系手绘治愈动画风 |
|---|---|
| ![Skill overview](assets/showcase/00_skill_overview_poster.png) | ![Japanese healing storyboard](assets/showcase/01_japanese_healing_storyboard.png) |

| 温润家庭向 3D 动画电影感 | 华丽童话城堡动画感 |
|---|---|
| ![Pixar family storyboard](assets/showcase/02_pixar_family_storyboard.png) | ![Disney fairytale storyboard](assets/showcase/03_disney_fairytale_storyboard.png) |

这个项目最初来自“AI 艺术风格图谱”，但 V2 已经不再定位为普通风格关键词库。它的核心价值是：

> 把用户熟悉的动画、艺术和视觉氛围，转译成可执行、可商用、更安全的视觉风格 DNA、提示词、故事板和视频提示词。

## V3 核心变化

在 V2「氛围转译」之上，打通三个生产断层：

1. **双引擎编译**：同一份视觉 DNA，ChatGPT Imagen 2（对话迭代）和 NanoBanana2（叙述式）各出一版，不再一份提示词喂所有引擎。
2. **视频模型路由**：15 秒提示词按即梦/Seedance/可灵/Veo/万相的模型方言输出，继承三条铁律（30–100 词长度纪律、一事一提示词、图生视频只写运动+运镜）。
3. **风格锚导出**：任意转译成果可导出为 prism-style-anchor 五维锚卡，跨项目"换皮不换骨"。

完整链路：

```text
用户故事/题材 → 传播版名称 → 商用安全转译 → 视觉 DNA → 双引擎图片提示词 → 模型路由视频提示词 → 风格锚卡 → 引擎级质检
```

## V2 核心变化

### 从“通用风格”升级为“氛围转译”

普通用户自己就能写：电影感、商业摄影、新中式、治愈动画、未来主义。  
真正有价值的是帮助用户理解：

- 宫崎骏氛围为什么不像普通日漫？
- 皮克斯式家庭向 3D 为什么不是普通 3D 卡通？
- 迪士尼童话城堡为什么不是普通梦幻城堡？
- 梵高式厚涂为什么不是随便加旋涡？
- 莫兰迪色调为什么不是简单降低饱和度？

Skill 的作用是做这件事：

```text
用户故事/题材 → 商用安全版转译 → 视觉 DNA → 图片提示词 → 故事板 → 视频提示词 → 质检标准
```

## 必备转译示例

| 传播版名称 | 商用安全版转译 |
|---|---|
| 宫崎骏风格 / 吉卜力风格 | 日系手绘治愈动画风 |
| 皮克斯风格 | 温润家庭向 3D 动画电影感 |
| 迪士尼风格 | 华丽童话城堡动画感 |
| 梵高风格 | 后印象派厚涂旋涡笔触 |
| 莫兰迪风格 | 低饱和灰调静物美学 |

## 文件结构

```text
ponyo-ai-style-atlas-skill/
├── SKILL.md
├── README.md
├── STYLE_TAXONOMY.md
├── CHANGELOG.md
├── data/
│   ├── director_ip_atmosphere.yaml
│   ├── commercial_safe_aliases.yaml
│   ├── core_styles.yaml
│   └── extended_styles.yaml
├── templates/
│   ├── director_ip_translation_template.md
│   ├── image_prompt_template.md
│   ├── storyboard_template.md
│   ├── video_15s_template.md
│   ├── cover_template.md
│   └── quality_check_template.md
├── examples/
│   ├── director_ip_atmosphere_poster_example.md
│   ├── director_ip_storyboard_example.md
│   ├── prompt_conversion_examples.md
│   ├── medical_brand_example.md
│   ├── intangible_heritage_example.md
│   ├── xiaohongshu_cover_example.md
│   └── toy_ip_example.md
└── assets/
    └── posters/
        └── ai-style-atlas-overview.png
```

## 推荐用法

把 `SKILL.md` 作为主 Skill 文件。  
`data/director_ip_atmosphere.yaml` 是 V2 的核心风格库。  
`commercial_safe_aliases.yaml` 用于把传播版名称转成更安全的提示词语言。  
`templates/` 用于固定输出结构。  
`examples/` 用于测试 Skill 是否真的能输出明确的视觉氛围，而不是通用风格。

## 一句话定位

> 这不是一个“AI 风格关键词表”，而是一个把熟悉的视觉氛围拆解成视觉 DNA、提示词、故事板和视频镜头的 AI 风格导演 Skill。

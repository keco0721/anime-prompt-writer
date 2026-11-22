---
name: anime-prompt-writer
description: 写二次元生图的角色提示词与场景提示词，两者分开写——角色行只负责触发角色（官方角色 tag + 辨识点，短），场景行只负责背景/光线/镜头，姿态另起一行，每次给完整可粘贴版本。
whenToUse: 写角色提示词、场景提示词、生图 prompt，或要求换姿势/换构图/换背景/改光线、给某个角色写 tag 时。
---

# 二次元提示词 · 角色与场景分开写

三块各管一件事，不许越界：**角色行只触发角色，场景行只写画面，姿态行只写动作**。默认照做，不要问格式。

## 交付习惯

1. 每次给**完整版**（能直接粘贴的全量），不要只给改动片段。
2. 英文提示词 + 中文要点 2–3 行，只讲这版改了什么、为什么。
3. 不加权重括号、不写解释性括注、不追问。
4. 迭代只换该换的那一行，其余原样保留。

## 一、角色行：只负责「让模型认出是谁」

角色行的唯一任务是命中角色。写得再细，没命中就是别人；命中了，多余的描述只会干扰。

写法：`1girl, solo, 角色 tag` → 发型发色 → 瞳色 → 一眼能认出的服饰/标志物。**25–30 个词就够**。

- **角色 tag 优先**：`roxy migurdia` / `sunna (zenless zone zero)` / `vodyanitsa (genshin impact)`。带作品名的最稳；库里有就照抄，别改写。
- **只补辨识点**：能让屏幕外的人一眼认出是谁的那几项（双马尾+呆毛、白色光环、白色狼耳灰狼尾）。衣服只写到"穿的是什么"，花纹、褶边、层次留给生成。
- **只写看得见的东西**：形状、颜色、朝向、位置、长度。名词概念要拆开写。反面：`鲸鳍耳`、`精灵感长发`；正面用位置+颜色+形状描述，例如 `two slim fins on both sides of her head in place of ears, navy upper side with tiny white dots, bright white lower edge`。
- **角色行不写**：性格、情绪（`gentle`/`elegant`）、姿态、背景、光线、镜头。这些一律不进来。
- **换装**：核心块不动，只加服装行；把角色原有服装 tag 写进负面（`witch hat, robe`），否则新旧衣服打架。
- **库外角色**：先找官方立绘或游戏内模型看过再写，不凭印象编；写完不建模就只当一次性用。

现成角色块见 `references/角色块库.md`（洛琪希、sunna、huohuo、norma、lappland、skirk、furina、kei、arona、sylphiette、phoebe）。

## 二、场景行：只负责背景 / 光线 / 镜头

三行各写各的，每行独立，互不串词。

### 背景

先定底，再叠元素，最后写**元素怎么消失**。消失要写过程，不是写 `smooth transition`：

```
pure white background, the milky way confined to the top quarter, fading by real atmospheric falloff rather than a mask: star density drops first and the clusters break into loose scattered stars, then the nebula thins into smoke-like wisps desaturating from blue-violet to pale lavender grey, then the remaining stars lose contrast one by one, a soft irregular edge made of drifting haze instead of a clean line, fully gone before it reaches her head
```

四类底（按常用程度：白棚 31%、星空 19%、实景 18%、纯黑 18%）：

| 底 | 写法 | 关键 |
|---|---|---|
| 纯白棚 | `pure white background, seamless white void, subtle floor shadow` | 靠轮廓光把人和白分开 |
| 纯黑 low-key | `pure black background, low-key lighting, thin cool rim light tracing her silhouette` | 黑要发亮只能靠轮廓光和暖光溢出 |
| 星空/银河 | `confined to the top quarter` + 密度→颜色→对比依次衰减 | 别占满画面，别在肩上截止 |
| 自然实景 | 灰山 `grey mountains fading into mist`、水面 `shallow clear water with ripples and caustics`、树影 | 加浅景深和前景虚化拉开层次 |

### 光线

`方向 + 光质 + 阴影形状 + 轮廓光 + 氛围`

```
hard key from upper left, shaped cool shadows on the right half, mint and cyan rim on ponytail and arm, soft fill keeping shadow detail, subsurface scattering, gradient skin shading, one wide rainbow arc behind her waist, rainbow caustics on skirt, rainbow bokeh in the lower foreground, strong bloom on hair edges, high key
```

常用件：`hard key` / `soft even key` / `strong backlight` / `rim light separating her from the background` / `subsurface scattering`（皮肤透） / `bloom`（光晕） / `caustics`（水光） / `bokeh`（前景虚化光斑） / `high key`（通透） / `low-key`（暗调）。

要"清透光感强"：加 `bloom + rainbow bokeh + subsurface scattering + high key`，光斑放**前景虚化**，别糊脸上。

### 镜头

`景别 + 焦段 + 机位 + 构图位置 + 留白`

```
medium shot, centered composition, eye level, 50mm
```

- 景别：`full body`(63) / `medium shot`(98) / `half body`(20) / `close-up`(24)
- 焦段：**50mm 是默认**（74 次），特写用 85mm(23)，环境带走 35mm(28)
- 机位：`eye level`(46) 或 `slight low angle`(41)
- 构图：**默认居中** `centered composition`(61)；要三分才写 `subject on the right third, generous negative space`
- 全身必须加 `full figure uncropped`
- **禁鱼眼、禁超广角畸变**（除非明确要夸张构图）

## 三、姿态行：只负责动作与表情

既不属于角色也不属于场景，单独一行。写不对称：`one shoulder lifted`、`chin tucked`、`weight on back leg, front knee bent`、`head tilted slightly`。两只手要各自有事做（撑、扶、拨头发、拿东西），别写成对称站桩。表情写可见的肌肉与朝向：`gentle smile, looking at viewer`、`lips slightly parted`、`half-lidded gaze sliding sideways`。

## 四、画风收尾

按常用程度：`cel shading`(178) > `thin lineart`(158) > `very aesthetic`(106) > `absurdres`(102) > `painterly rendering`(62) > `clean crisp lineart`(49)。

默认尾：`cel shading, thin lineart, painterly rendering, high clarity, low noise`

要做「流萤那套」的光感版本，整条尾换成 `references/风格块库.md` 里的风格块（逆光 + bloom + 彩虹色差 + 花粉尘三件套），别和默认尾混着写。

## 五、负向块

分两类写，别混成一坨。

**人物类**（角色行/姿态行出问题时用）：

```
lowres, bad hands, extra fingers, extra characters, text, watermark, exposed chest, plastic skin, stiff pose, cropped feet
```

**画面类**（场景行出问题时用）：

```
grey background, cluttered background, props, muddy colors, flat lighting
```

按底追加：白棚加 `floor line`；星空加 `clean line edge, hard boundary in the sky`；黑底加 `grey background, visible backdrop`。**换装时把角色原有服装 tag 写进负向**（否则新旧服装会打架）。

## 参考文件

- `references/角色块库.md`：洛琪希（已核，含四套换装）+ sunna / huohuo / norma / lappland / skirk / furina / kei / arona / sylphiette / phoebe 短块。
- `references/场景词库.md`：按常用程度排序的背景/光线/镜头/负向高频词。
- `references/风格块库.md`：花海逆光那套（光即主角 + 花粉/光斑/彩虹色差 + 粉彩配色）的风格尾块、四类常驻服装块、四个高频场景块。

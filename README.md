# ClawMate

[English](./doc/README.en.md) | 中文

> 为 OpenClaw 添加一个有温度的角色伴侣。

她知道现在几点，知道你在做什么。你问她在哪，她就告诉你；你不问，她也可能随手发来一张自拍。

---

## 🎉 最新更新

### v1.1.0 (2026-03)

- 📸 **新增第三方视角拍摄模式（boyfriend）** — 支持男友视角拍摄，包含多种拍摄角度（俯视、仰视、侧面、背影等）、距离（近景、中景、远景）和构图方式
- 🎭 **智能姿势随机系统** — 根据 SKILL.md 中定义的时间段姿势库，自动随机选择拍照角度、动作和姿势，让每次生图更自然多样（需要提前在SKILL.md中设定各个时间段，每个时间段的拍照姿势，每个时间段的姿势库可预设计50+，生图时会自动在从50+中随机选定一个来进行生图）
- 🎬 **新增视频生成接口** — 支持通过配置调用第三方视频生成服务（如 Grok Video），基于生成的图片创建短视频


---

## 功能

- **时间感知** — 早晨、上课、午休、傍晚、深夜，场景和穿搭随时间自动切换
- **情境生图** — 根据对话内容和当前状态生成自拍（支持写实和动漫风格），非模板套用
- **多视角拍摄** — 支持三种拍摄模式：
  - `direct`：普通自拍视角
  - `mirror`：对镜全身照
  - `boyfriend`：第三方视角（男友视角），支持多种拍摄角度（俯视、仰视、侧面、背影）、距离和构图
- **智能姿势系统** — 根据时间段从 SKILL.md 预设姿势库中随机选择拍照角度、动作和姿势
- **主动发图** — 可配置触发频率，日常聊天中随机发自拍表示关心
- **视频生成** — 基于生成的图片调用第三方服务生成短视频（实验性功能）
- **多角色** — 每个角色有独立人设、时间状态和参考图，通过配置一键切换
- **自定义角色** — 通过对话创建自定义角色，LLM 引导生成完整角色定义并写盘
- **多图像服务** — 支持阿里云百炼、火山引擎 ARK、fal.ai、OpenAI 兼容接口

## 应用场景

- **个人伴侣** — 日常陪伴、情感交流、生活助手
- **虚拟导师** — 学习辅导、知识答疑、进度跟踪
- **智能客服** — 企业服务、品牌形象、客户互动
- **专业顾问** — 健康管理、心理咨询、职业指导

## 开发计划

- [x] **多视角拍摄** — 支持第三方视角（男友视角）和多种拍摄角度
- [x] **智能姿势系统** — 基于时间段的姿势库随机选择
- [x] **视频生成** — 短视频片段生成（实验性）
- [ ] **更多角色** — 添加不同性格和背景的内置角色
- [ ] **语音交互** — 角色语音合成，支持语音对话
- [ ] **动态表情** — 更丰富的表情和动作库
- [ ] **社区角色** — 角色分享和下载平台

---

## 效果展示

### 对话界面

<div align="center">
  <a href="doc/images/demo/demo.png">
    <img src="doc/images/demo/demo1.png" width="45%" alt="指定场景" />
  </a>
  <a href="doc/images/demo/demo2.png">
    <img src="doc/images/demo/demo2.png" width="45%" alt="不指定场景" />
  </a>
  <br/>
  <sub>左：指定场景 | 右：不指定场景</sub>
</div>

### 生成效果

更多样例图片见 [完整图片展示](doc/images/demo/README.md)

<div align="center">
  <img src="doc/images/demo/1.jpg" width="45%" alt="场景示例1" />
  <img src="doc/images/demo/6.jpg" width="45%" alt="场景示例2" />
  <br/>
  <img src="doc/images/demo/8.jpg" width="45%" alt="场景示例3" />
  <img src="doc/images/demo/9.jpg" width="45%" alt="场景示例4" />
  <br/>
  <sub>不同时间状态和场景下的自动生成效果</sub>
</div>


---

## 快速开始

确保已安装 [OpenClaw](https://github.com/openclaw/openclaw)。

### 安装 / 更新

首次安装与后续更新使用同一命令：

```bash
npx github:BytePioneer-AI/clawmate
```

交互式安装向导会引导你完成角色选择、主动发图配置和图像服务配置。

安装完成后，对你的 Agent 说：

```
发张自拍看看
你现在在干嘛？
晚上在卧室穿着粉色睡衣拍一张
帮我拍一张（自动使用第三方视角，随机选择姿势和角度）
```

创建自定义角色:
```
帮我创建一个[动漫/写实]风格的新角色，她是一个[描述职业/性格/背景]的女生

# 例：
帮我创建一个动漫风格的新角色，她是一个喜欢画画的大学生
帮我创建一个写实风格的新角色，她是一个热爱咖啡的独立书店店长
```

## 本地开发

```bash
git clone https://github.com/BytePioneer-AI/clawmate.git
cd clawmate
npm install
npm run clawmate:setup
```

---

## 图像服务配置

在 `~/.openclaw/openclaw.json` 的 `plugins.entries.clawmate-companion.config` 下配置：

### 服务特点与选型建议
> - 写实风格建议使用 Nano Banana。  
> - 除 Nano Banana 外，其他模型更建议搭配动漫角色。

| 服务 | 费用特性 |
| --- | --- |
| ModelScope | 完全免费 |
| 阿里云百炼 | 有免费额度（以官方控制台为准） |
| 火山引擎 ARK | 有免费额度（以官方控制台为准） |
| OpenAI 兼容接口 | 取决于接入服务商 |
| fal.ai | 取决于平台计费策略 |




**OpenAI 兼容接口**
```json
{
  "defaultProvider": "openai",
  "providers": {
    "openai": {
      "name": "openai",
      "apiKey": "YOUR_OPENAI_API_KEY",
      "baseUrl": "https://api.openai.com/v1",
      "model": "gpt-image-1.5"
    }
  }
}
```

支持任何兼容 OpenAI `/v1/images/edits` 接口的服务，可通过 `baseUrl` 指定自定义端点。

**阿里云百炼**

```json
{
  "defaultProvider": "aliyun",
  "providers": {
    "aliyun": {
      "apiKey": "YOUR_DASHSCOPE_API_KEY",
      "model": "wan2.6-image"
    }
  }
}
```

**火山引擎 ARK**（[API申请文档](doc/API申请文档.md)）
```json
{
  "defaultProvider": "volcengine",
  "providers": {
    "volcengine": {
      "apiKey": "YOUR_ARK_API_KEY",
      "model": "doubao-seedream-4-5-251128"
    }
  }
}
```

**fal.ai**
```json
{
  "defaultProvider": "fal",
  "providers": {
    "fal": {
      "apiKey": "YOUR_FAL_KEY",
      "model": "fal-ai/flux/dev/image-to-image"
    }
  }
}
```


---

## 视频生成配置（实验性功能）

在 `~/.openclaw/openclaw.json` 的 `plugins.entries.clawmate-companion.config` 下配置：

```json
{
  "videoProvider": "grokvideo",
  "providers": {
    "grokvideosougou": {
      "apiKey": "YOUR_GROK_API_KEY",
      "baseUrl": "https://api.x.ai/v1",
      "model": "grok-imagine-1.0-video",
      "timeoutMs": 300000
    }
  }
}
```

视频生成基于已生成的图片，通过第三方服务（如 Grok Video）创建 6 秒短视频。

---

## 主动发图

```json
{
  "proactiveSelfie": {
    "enabled": true,
    "probability": 0.1
  }
}
```

`probability` 为每条消息的触发概率，推荐范围 `0.1`–`0.3`。

---

## 多角色

### 内置角色

在 `assets/characters/` 下新建角色目录，包含：

```
{character-id}/
├── meta.json           # id、name、style（photorealistic/anime）、timeStates
├── character-prompt.md # 角色人设（英文）
├── README.md           # 角色档案（中文）
├── images/             # 参考图文件夹
│   └── reference.png
└── *.png               # 其他参考图（可选）
```

然后在配置中切换：

```json
{
  "selectedCharacter": "your-character-id"
}
```

### 自定义角色（对话创建）

直接对 Agent 说：

```
帮我创建一个新角色，她是一个喜欢画画的大学生
```

Agent 会调用 `clawmate_prepare_character` 获取角色定义模板和样例，引导你补充细节，然后调用 `clawmate_create_character` 将角色写入 `~/.openclaw/clawmeta/`。

自定义角色目录与内置角色分离，加载时用户目录优先。也可以通过配置 `userCharacterRoot` 自定义存储路径。

---

## 项目结构

```
ClawMate/
└── packages/clawmate-companion/
    ├── src/core/          # 核心逻辑（pipeline、router、providers）
    ├── skills/            # Skill 定义与角色素材
    │   └── clawmate-companion/
    │       ├── SKILL.md
    │       └── assets/characters/
    │           └── brooke/
    └── bin/cli.cjs        # 安装向导
```

---

## License

MIT

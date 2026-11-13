# aisee-runninghub-video

使用 RunningHub 在线工作流（浏览器界面）制作分段视频并合并成片的 Agent Skill。

## 工作流概览

1. **引导登录** — 给用户 RunningHub 链接，请用户自行登录并回复「继续」。
2. **人物与场景图片** — 按剧情人设生成，给用户审核，不满意可提修改意见。
3. **剧本** — 生成剧本给用户审核，节奏快、剧情推进快。
4. **分段提示词** — 根据剧本生成分段提示词，用 MiniMax H3 官方 skill 加工。
5. **逐段生成视频** — 浏览器后台运行在线工作流（不走 API）：52 节点放参考图，69 节点设提示词/分辨率/画面比例/每段时长（不动其他设置），640p 以下用运行 lite/standard、720p 以上用运行 lite/plus；运行几分钟后的报错忽略，关掉报错窗口在 79 节点取分段视频。
6. **合并交付** — 各分段视频合并为一个成片交付给用户。

每段可生成 5-15 秒视频、1-5 个分镜。

## 安装

使用 [skills CLI](https://github.com/vercel-labs/skills) 安装：

```bash
# 列出本仓库中的 skill
npx skills add annalyseg805-blip/aisee-runninghub-video --list

# 安装
npx skills add annalyseg805-blip/aisee-runninghub-video --skill aisee-runninghub-video
```

或直接克隆：

```bash
git clone https://github.com/annalyseg805-blip/aisee-runninghub-video.git
```

## 文件说明

- `SKILL.md` — skill 主文件，含 frontmatter（name / description）与完整工作流。
- `LICENSE` — MIT。

## 参考

- 提示词加工：[MiniMax H3 skills](https://github.com/MiniMax-AI/MiniMax-H3/tree/main/skills)
- RunningHub 工作流：https://www.runninghub.cn/post/2120034062739009538

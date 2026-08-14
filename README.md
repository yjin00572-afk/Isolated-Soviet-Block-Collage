# Isolated Soviet Block Collage

## 安装位置

当前 skill 安装在你的agent的skill文件夹下面，例如codex：

`C:\Users\LENOVO\.codex\skills\isolated-soviet-block-collage`

还可以直接发给你的agnet:请为我安装这个skill，链接是https://github.com/yjin00572-afk/Isolated-Soviet-Block-Collage.git

主要文件：

- `SKILL.md`：skill 主规则与默认执行协议
- `agents/openai.yaml`：Codex UI 元数据
- `references/prompt-contract.md`：可复用的提示词骨架、负面提示和验收清单

## 默认工作流

这个 skill 当前已经内置“先给方案，再生成”的默认协议。

默认执行顺序：

1. 读取原图和参考图
2. 输出一版简明方案
3. 给出最终 prompt 和 negative prompt
4. 如果有可用图像生成或编辑工具，则继续在同一任务内生成结果
5. 如果第一轮结果违反外区保真、块内隔离、源色限制或比例限制，则收紧提示词再重试一次

只有在用户明确要求“先确认”“先看方案”“先别生成”时，流程才会停在方案阶段。

## 使用方式

### 1. 直接调用 skill

```text
Use $isolated-soviet-block-collage on this image.
```

### 2. 先给方案，再生成(我抖音的实例图片)

```text
Use $isolated-soviet-block-collage 先给方案，再生成。
```

### 3. 只要提示词，不要生成

```text
Use $isolated-soviet-block-collage 给我最终 prompt，不要直接生成。
```

### 4. 直接应用到图片

```text
Use $isolated-soviet-block-collage 直接应用到这张图。
```

## 输出内容

正常情况下，这个 skill 会先产出以下内容：

- 原图诊断
- 提取出的主色
- 内部块布局方案
- 每个块内部的重绘计划
- 最终 prompt
- negative prompt
- 简短验收清单

如果图像工具可用，并且用户没有要求暂停，它会继续生成图片结果。

## 举例图片
<img width="1023" height="1537" alt="0ba985ec804b19f13f20d334e656bf84" src="https://github.com/user-attachments/assets/70a67b96-1fcc-4f0c-aad5-4f52c4990e3e" />

## 常见失败情况

如果结果出现以下问题，通常说明提示词需要收紧：

- 整张图都被风格化了
- 外区被重绘或变色了
- 线稿溢出到块外
- 内部块颜色与原图无关
- 块像平面贴纸，没有厚度或阴影
- 块内内容不是对原图遮挡区域的重绘，而是随机新图

## 适合搭配的使用方式

这个 skill 最适合和图像编辑工具一起使用：

- 先由 skill 产出高约束提示词
- 再将该提示词交给图像生成或编辑工具执行

如果你只想拿提示词，这个 skill 也可以只停留在方案输出阶段。

## 常见失败情况

如果结果出现以下问题，通常说明提示词需要收紧：

- 整张图都被风格化了
- 外区被重绘或变色了
- 线稿溢出到块外
- 内部块颜色与原图无关
- 块像平面贴纸，没有厚度或阴影
- 块内内容不是对原图遮挡区域的重绘，而是随机新图


##  GitHub 的仓库结构


```text
isolated-soviet-block-collage/
├─ SKILL.md
├─ README.md
├─ LICENSE.txt
├─ NOTICE
├─ .gitignore
├─ agents/
│  └─ openai.yaml
└─ references/
   └─ prompt-contract.md
```

## 版权与授权

当前仓库默认采用 Apache License 2.0。

- 许可证文件：`LICENSE.txt`
- 版权归属说明：`NOTICE`

感谢您的观看，这是我第一次制作skill，有任何意见和问题欢迎抖音@Breathe ，也欢迎您来玩这个skill发抖音可以@Breathe ，让我欣赏您的作品。

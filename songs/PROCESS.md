# 纯合成音乐制作说明

**原创声明：本目录全部音频均为 Python（NumPy/SciPy）从零合成的原创作品；不读取、不采样任何现有音频，无采样、无翻唱、无混音，未使用现成旋律或 MIDI 文件。** 所有鼓、贝斯、和声、钢琴、主旋律及元音颗粒均由代码生成波形。内部采用 44.1 kHz、32-bit float 计算，WAV 导出为 16-bit PCM，MP3 由 ffmpeg 以 320 kbps 转码。

十首都采用固定且不同的随机种子。总线使用 tanh 软饱和，峰值目标不超过 -1 dBFS；重渲染后实测全曲 RMS 为 -14.08 ~ -16.08 dBFS（峰值 -1.00 dBFS）。Kick/Bass 居中单声道；Pad、Hat、延迟和混响扩宽。Kick 对 Bass/Pad 施加 6.5 dB 侧链下压。延迟为多抽头衰减结构，混响为反馈 Comb 与 All-pass 组合，无外部脉冲响应。

每首先写作双小节原创动机，以级进为主、跳进后回到邻近音解决；乐句按 70% 原样复现、30% 固定规则变奏排列。鼓和 Lead 使用微时值与 ±10% 力度抖动。元音切片由脉冲源和 a/i 共振峰生成，以 30–80 ms 颗粒重排并进行 ±3 半音播放速率移调。段落边界设置短呼吸间隙，仅保留效果尾音与滤波噪声。

## 01. Daybreak Static

- 实测目标时长：120.000 秒（62 小节）；A minor，124 BPM。
- 和声进行：Am–F–C–G；主节奏：UK garage / 2-step。
- 结构 A：Intro 8s / Verse 16s / Pre-chorus 16s / Drop1 16s / Breakdown 16s / Verse2 16s / Drop2 16s / Outro 16s，按 BPM 对齐为整数小节。
- 配器：正弦扫频 Kick、多段噪声 Snare/Clap、高通 Hat、Sub、短促 9 泛音钢琴、玻璃感失谐垫、双振荡器 Lead、Conga 与元音颗粒。

## 02. Calle Luna

- 实测目标时长：120.000 秒（52 小节）；D minor，104 BPM。
- 和声进行：Dm–Gm–Bb–A；主节奏：Dembow。
- 结构 B：Intro 12s / Verse 20s / Chorus 20s / Break 16s / Chorus2 20s / Bridge 12s / Outro 20s，按 BPM 对齐为整数小节。
- 配器：Dembow 低鼓与切分军鼓组、共振 Conga、圆润 Sub、三度/五度钢琴音簇、暗色三角/锯齿垫与 a/i 元音颗粒。

## 03. Rain on the Balcony

- 实测目标时长：120.000 秒（63 小节）；F# minor，130 BPM。
- 和声进行：F#m–C#m–D–E；主节奏：2-step。
- 结构 A：Intro / Verse / Pre-chorus / Drop1 / Breakdown / Verse2 / Drop2 / Outro，权重为 8/16/16/16/16/16/16/16 秒并量化到小节。
- 配器：雨点感高通 Shaker、宽立体声 Pad、9 组衰减泛音钢琴、少量滑音和 5.2 Hz 颤音 Lead、侧链 Sub。

## 04. Two-Step Heart

- 实测目标时长：120.000 秒（54 小节）；G minor，108 BPM。
- 和声进行：Gm–Eb–Bb–F；前半 Dembow，后半切换为 2-step。
- 结构 C：Intro 8s / Verse 24s / Drop 24s / Piano-break 16s / Drop2 24s / Outro 24s，按 BPM 对齐为整数小节。
- 配器：两种鼓组的 arranged transition、低/高共振 Conga、暖 Sub、钢琴断奏、Piano-break 中突出的衰减泛音与呼吸尾音。

## 05. Neon Confession

- 实测目标时长：120.000 秒（58 小节）；C minor，116 BPM。
- 和声进行：Cm–Ab–Eb–Bb；2-step / Dembow 逐小节 50/50 融合。
- 结构 A：Intro / Verse / Pre-chorus / Drop1 / Breakdown / Verse2 / Drop2 / Outro，按 8/16/16/16/16/16/16/16 秒权重量化。
- 配器：交替鼓组、霓虹感慢 LFO 宽垫、9 泛音钢琴、失谐锯齿/三角双 Lead、多抽头立体声延迟和共振峰切片。

## 06. Letters I Never Sent

- 实测目标时长：120.000 秒（50 小节）；E minor，98 BPM。
- 和声进行：Em–D–C–B；主节奏：Dembow。
- 结构 B：Intro / Verse / Chorus / Break / Chorus2 / Bridge / Outro，按 12/20/20/16/20/12/20 秒权重量化。
- 配器：低速 Dembow、木质 Conga、稀疏钢琴、近场共振峰元音颗粒、低通包络 Sub 与反馈混响尾音。

## 07. Midnight Merengue

- 实测目标时长：120.000 秒（64 小节）；Bb minor，128 BPM。
- 和声进行：Bbm–Ab–Gb–F；主节奏：2-step。
- 结构 C：Intro / Verse / Drop / Piano-break / Drop2 / Outro，按 8/24/24/16/24/24 秒权重量化。
- 配器：高速切分 2-step、短噪声瞬态 Kick、多段 Clap、明亮 Hat、午夜感失谐和弦垫与错位元音颗粒。

## 08. Glasshouse

- 实测目标时长：120.000 秒（56 小节）；Eb minor，110 BPM。
- 和声进行：Ebm–Db–B–Gb；2-step / Dembow 融合。
- 结构 A：Intro / Verse / Pre-chorus / Drop1 / Breakdown / Verse2 / Drop2 / Outro，按 8/16/16/16/16/16/16/16 秒权重量化。
- 配器：融合鼓组、透明交叉反馈延迟、失谐锯齿 Pad、微失谐钢琴泛音、滤波呼吸噪声和 ±3 半音颗粒人声。

## 09. Salt Air

- 实测目标时长：120.000 秒（53 小节）；B Dorian，106 BPM。
- 和声进行：Bm–E–A–F#m；主节奏：Dembow。四个和弦的和弦音全部落在 B Dorian 音阶内。
- 结构 B：Intro / Verse / Chorus / Break / Chorus2 / Bridge / Outro，按 12/20/20/16/20/12/20 秒权重量化。
- 配器：Dorian 特征音级动机、Dembow Kick/Snare、空气感 Shaker、开阔 LFO Pad、居中 Sub 与扩宽延迟。

## 10. Coming Home Slow

- 实测目标时长：120.000 秒（61 小节）；F Dorian，122 BPM。
- 和声进行：Fm–Bb–Eb–Ab；主节奏：极简 2-step。四个和弦的和弦音全部落在 F Dorian 音阶内。
- 结构 C：Intro / Verse / Drop / Piano-break / Drop2 / Outro，按 8/24/24/16/24/24 秒权重量化。
- 配器：减少 Kick 与 Conga 密度的极简鼓组、长释放 Pad、低密钢琴、克制双振荡器 Lead、明显的段落呼吸间隙。

## 复现与校验

```bash
python synth.py
python verify.py
```

`python synth.py --only 1` 可单独渲染第一首；默认依次生成全部 WAV 与 MP3。`verify.py` 对 20 个输出文件逐一执行解码、时长、峰值、静音段、10 秒 RMS 动态方差检查，并额外检查 WAV 的 PCM16/采样率和 MP3 的 320 kbps 码率；详细结果写入 `verify_report.txt`。

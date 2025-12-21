# Omni-Project-Stats (全项目统计工具)

一个单文件、零依赖、跨平台的通用项目统计工具。

它不仅能统计代码（智能去除注释与空行），还能深入统计美术资源、音频、游戏工程文件等，特别适合**游戏开发**、**多媒体项目**或**全栈工程**的体量分析。

## ✨ 核心特性

*   **双模运行**：
    *   🖥️ **GUI 模式**：双击即用，提供现代化图形界面，一键扫描，实时日志，支持生成可视化图表。
    *   ⌨️ **CLI 模式**：命令行运行，支持自动化脚本集成，输出详细文本报告。
*   **全能统计**：
    *   **代码**：支持 C/C++, C#, Python, JS/TS, Java, Go, Rust, Lua, Shader (HLSL/GLSL) 等 50+ 种语言。
    *   **资源**：识别 3D 模型 (FBX/OBJ/Blend), 2D 贴图 (PSD/PNG/TGA), 音频 (WAV/MP3/Wwise), 视频等。
    *   **引擎**：深度识别 Unity, Unreal, Godot, RPG Maker, Cocos 等工程文件。
*   **智能分析**：
    *   精准剥离注释（支持 `//`, `/* */`, `#`, `<!-- -->`, `rem` 等多种风格）。
    *   自动忽略二进制文件与常见干扰目录（`.git`, `node_modules` 等）。
*   **零依赖**：
    *   基于 Python 标准库编写 (`tkinter`, `argparse`, `pathlib`)。
    *   无需 `pip install`，下载单文件 `project_stats.py` 即可运行。
*   **可视化报表**：
    *   一键生成 `project_stats_report.html`。
    *   内嵌 ECharts 图表，直观展示代码量分布、资源大小占比。

---

## 🚀 快速开始

### 1. 启动图形界面 (GUI)

直接运行脚本（不带参数）：

```bash
python project_stats.py
```

*   **操作**：点击 `📂 选择项目文件夹` -> 勾选选项 -> 点击 `🚀 开始扫描项目`。
*   **结果**：扫描完成后，可点击底部的 `🌐 在浏览器打开报告` 查看详细图表。

### 2. 命令行使用 (CLI)

在终端中指定路径：

```bash
python project_stats.py /path/to/your/project
```

生成 HTML 报告并统计资源文件：

```bash
python project_stats.py . --html --assets
```

---

## 📖 命令行参数详解

### 默认统计内容（无需配置）

工具默认会输出以下核心统计信息：
- ✅ **文件类型统计** - 各类文件的数量分布
- ✅ **代码统计** - 每种编程语言的文件数、代码行数（去除空行和注释）、总字符数及占比
- ✅ **文件总数** - 项目中统计到的文件总数

### 可选参数

| 参数 | 说明 |
| :--- | :--- |
| `path` | **必选** (仅 CLI 模式)。项目根目录路径，默认为当前目录 `.`。 |
| `--html [FILE]` | 生成交互式 HTML 可视化报告。可指定文件名，默认 `project_stats_report.html`。 |
| `--assets` | **强烈推荐**。额外统计非代码/资源文件（图片、音频、模型、二进制数据等）。 |
| `--detail` | 输出细分统计（按文件后缀名分类展示）。例如：样式文件细分为 `.css`、`.scss`、`.less`；图片文件细分为 `.png`、`.jpg`、`.webp` 等。 |
| `--list-files` | 输出所有被统计文件的相对路径清单。 |
| `--log [FILE]` | 将统计结果输出到文本文件。可指定文件名，默认 `project_stats.log`。 |
| `--no-ignore` | 不忽略常见目录（如 `.git`, `node_modules`, `dist` 等）。慎用，会导致统计结果虚高。 |
| `--include-hidden` | 包含隐藏文件（以 `.` 开头的文件或目录）。 |

### 常见用法示例

**场景 1：统计当前目录代码（CLI 模式）**
```bash
python project_stats.py .
```
*(注：如果不带 `.` 参数，将默认启动 GUI 界面)*

**场景 2：统计游戏项目（含美术资源）并生成报表**
```bash
python project_stats.py "D:/UnityProjects/MyGame" --assets --html
```

**场景 3：查看所有被统计的文件列表**
```bash
python project_stats.py . --list-files
```

---

## 🛠️ 支持的语言与格式

本工具内置了 **100+ 种** 文件后缀识别规则，覆盖 90% 的开发场景：

*   **编程语言**: C, C++, C#, Java, Kotlin, Swift, Objective-C, Python, Ruby, PHP, Go, Rust, Dart, Lua, Perl, R, Shell, Batch, PowerShell...
*   **Web 开发**: HTML, CSS, SCSS, Less, JavaScript, TypeScript, JSON, XML, YAML, TOML, WASM...
*   **游戏引擎**: Unity (.unity, .prefab), Unreal Engine (.uasset), Godot (.gd, .tscn), RPG Maker, Ren'Py, Cocos/Laya (JS/TS)...
*   **图形渲染**: Shader (HLSL/GLSL/CG), Material, Texture...
*   **美术资源**:
    *   **2D**: Photoshop (PSD/PSB), Illustrator (AI), Aseprite, Clip Studio Paint, SAI, Krita...
    *   **3D**: FBX, OBJ, GLTF/GLB, Blender, Maya, 3ds Max, Cinema 4D...
    *   **动画**: Spine 2D, Live2D (Cubism)...
*   **音频视频**: DAW工程 (FL Studio/Cubase/Logic), 音频中间件 (Wwise/FMOD/ADX2), WAV/MP3/MP4/MOV...
*   **策划文档**: Markdown, Office (Word/Excel/PPT), PDF, MindMap (XMind), Axure, Draw.io...

---

## ❓ 常见问题 (Q&A)

**Q: 为什么生成的报告中“资源总大小”显示为 0 B？**
A: 资源统计是一项可选功能（为了提高纯代码统计的速度）。
*   **CLI 模式**: 请务必添加 `--assets` 参数。
*   **GUI 模式**: 请确保勾选了“统计资源文件”选项（默认已勾选）。

**Q: 双击脚本没有弹出界面，而是打开了代码编辑器？**
A: 这是因为 `.py` 文件被关联到了编辑器。
*   **解决方法 1**: 右键文件 -> 打开方式 -> 选择 Python。
*   **解决方法 2**: 在文件夹空白处右键 -> "在终端中打开" -> 输入 `python project_stats.py`。

**Q: 扫描速度非常慢，或者卡住了？**
A: 请检查是否扫描了包含大量文件的目录（如 `node_modules`, `.git` 等）。
*   本工具默认会自动忽略这些目录。
*   **请勿**随意开启 `--no-ignore` 选项，除非你确实需要统计它们。

---

## 📝 License

本项目开源，随意使用与分发。
Happy Coding! 🚀

---

# English Version

# Omni-Project-Stats

A single-file, zero-dependency, cross-platform universal project statistics tool.

It not only counts code (intelligently strips comments and blank lines), but also analyzes art assets, audio, game engine files, making it perfect for **game development**, **multimedia projects**, or **full-stack engineering** volume analysis.

## ✨ Core Features

*   **Dual-Mode Operation**:
    *   🖥️ **GUI Mode**: Double-click to run, modern graphical interface, one-click scanning, real-time logs, supports visualization charts.
    *   ⌨️ **CLI Mode**: Command-line execution, supports automation script integration, outputs detailed text reports.
*   **Comprehensive Statistics**:
    *   **Code**: Supports 50+ languages including C/C++, C#, Python, JS/TS, Java, Go, Rust, Lua, Shader (HLSL/GLSL), etc.
    *   **Assets**: Recognizes 3D models (FBX/OBJ/Blend), 2D textures (PSD/PNG/TGA), audio (WAV/MP3/Wwise), video, etc.
    *   **Engines**: Deep recognition of Unity, Unreal, Godot, RPG Maker, Cocos, and other project files.
*   **Smart Analysis**:
    *   Accurately strips comments (supports `//`, `/* */`, `#`, `<!-- -->`, `rem`, and other styles).
    *   Automatically ignores binary files and common interference directories (`.git`, `node_modules`, etc.).
*   **Zero Dependencies**:
    *   Built on Python standard library (`tkinter`, `argparse`, `pathlib`).
    *   No need for `pip install`, just download the single file `project_stats.py` and run.
*   **Visualization Reports**:
    *   Generate `project_stats_report.html` with one click.
    *   Embedded ECharts charts, visually displaying code distribution and asset size proportions.

---

## 🚀 Quick Start

### 1. Launch GUI

Run the script directly (without arguments):

```bash
python project_stats.py
```

*   **Operation**: Click `📂 Select Project Folder` -> Check options -> Click `🚀 Start Scanning Project`.
*   **Result**: After scanning, click `🌐 Open Report in Browser` at the bottom to view detailed charts.

### 2. Command-Line Usage (CLI)

Specify path in terminal:

```bash
python project_stats.py /path/to/your/project
```

Generate HTML report and count asset files:

```bash
python project_stats.py . --html --assets
```

---

## 📖 Command-Line Parameters

### Default Statistics (No Configuration Required)

The tool outputs the following core statistics by default:
- ✅ **File Type Statistics** - Distribution of various file types
- ✅ **Code Statistics** - File count, lines of code (excluding blank lines and comments), total characters, and percentages for each programming language
- ✅ **Total File Count** - Total number of files counted in the project

### Optional Parameters

| Parameter | Description |
| :--- | :--- |
| `path` | **Required** (CLI mode only). Project root directory path, defaults to current directory `.`. |
| `--html [FILE]` | Generate interactive HTML visualization report. Can specify filename, defaults to `project_stats_report.html`. |
| `--assets` | **Highly recommended**. Additionally count non-code/asset files (images, audio, models, binary data, etc.). |
| `--detail` | Output detailed statistics (classified by file extension). For example: Style files breakdown into `.css`, `.scss`, `.less`; images breakdown into `.png`, `.jpg`, `.webp`, etc. |
| `--list-files` | Output relative paths of all counted files. |
| `--log [FILE]` | Output statistics to a text file. Can specify filename, defaults to `project_stats.log`. |
| `--no-ignore` | Don't ignore common directories (like `.git`, `node_modules`, `dist`, etc.). Use with caution, may inflate results. |
| `--include-hidden` | Include hidden files (files or directories starting with `.`). |

### Common Usage Examples

**Scenario 1: Count current directory code (CLI mode)**
```bash
python project_stats.py .
```
*(Note: If no `.` argument is provided, GUI interface will launch by default)*

**Scenario 2: Count game project (including art assets) and generate report**
```bash
python project_stats.py "D:/UnityProjects/MyGame" --assets --html
```

**Scenario 3: View list of all counted files**
```bash
python project_stats.py . --list-files
```

---

## 🛠️ Supported Languages and Formats

This tool has built-in recognition for **100+ file extensions**, covering 90% of development scenarios:

*   **Programming Languages**: C, C++, C#, Java, Kotlin, Swift, Objective-C, Python, Ruby, PHP, Go, Rust, Dart, Lua, Perl, R, Shell, Batch, PowerShell...
*   **Web Development**: HTML, CSS, SCSS, Less, JavaScript, TypeScript, JSON, XML, YAML, TOML, WASM...
*   **Game Engines**: Unity (.unity, .prefab), Unreal Engine (.uasset), Godot (.gd, .tscn), RPG Maker, Ren'Py, Cocos/Laya (JS/TS)...
*   **Graphics Rendering**: Shader (HLSL/GLSL/CG), Material, Texture...
*   **Art Assets**:
    *   **2D**: Photoshop (PSD/PSB), Illustrator (AI), Aseprite, Clip Studio Paint, SAI, Krita...
    *   **3D**: FBX, OBJ, GLTF/GLB, Blender, Maya, 3ds Max, Cinema 4D...
    *   **Animation**: Spine 2D, Live2D (Cubism)...
*   **Audio & Video**: DAW projects (FL Studio/Cubase/Logic), Audio middleware (Wwise/FMOD/ADX2), WAV/MP3/MP4/MOV...
*   **Planning Documents**: Markdown, Office (Word/Excel/PPT), PDF, MindMap (XMind), Axure, Draw.io...

---

## ❓ Frequently Asked Questions (FAQ)

**Q: Why does the generated report show "Total Asset Size" as 0 B?**
A: Asset statistics is an optional feature (to improve pure code statistics speed).
*   **CLI Mode**: Make sure to add the `--assets` parameter.
*   **GUI Mode**: Ensure "Count Asset Files" option is checked (checked by default).

**Q: Double-clicking the script doesn't open the GUI, but opens a code editor instead?**
A: This is because `.py` files are associated with an editor.
*   **Solution 1**: Right-click file -> Open with -> Choose Python.
*   **Solution 2**: Right-click in folder blank area -> "Open in Terminal" -> Type `python project_stats.py`.

**Q: Scanning is very slow or stuck?**
A: Check if scanning directories with many files (like `node_modules`, `.git`, etc.).
*   This tool automatically ignores these directories by default.
*   **Don't** enable `--no-ignore` option casually unless you really need to count them.

---

## 📝 License

This project is open source, free to use and distribute.
Happy Coding! 🚀

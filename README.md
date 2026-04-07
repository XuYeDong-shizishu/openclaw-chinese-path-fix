plaintext
  

# PowerShell 中文路径万能读取方案
一套仅3行的PowerShell代码，彻底解决Windows环境下中文文件夹/文件名读取乱码、报错的世纪难题。

## ✨ 核心优势
- 极速性能：底层调用.NET原生IO接口，执行速度碾压PowerShell原生Get-Content、CMD、Python常规方案
- 完美兼容：原生支持中文/空格/特殊字符路径，强制UTF8编码杜绝乱码，全Windows版本通用
- 零门槛使用：无第三方依赖、无需转义配置，复制代码即可直接运行
- 极简高效：仅3行核心代码，开箱即用，无需复杂环境搭建

## 🚀 万能3行代码
```powershell
# 1. 获取桌面路径
$desktop = [Environment]::GetFolderPath("Desktop")

# 2. 查找目标文件夹
$folder = (Get-ChildItem $desktop -Directory | Where-Object { $_.Name -like "*关键词*" }).FullName

# 3. 读取文件（完美支持中文路径）
$content = [System.IO.File]::ReadAllText("$folder\文件.md", [System.Text.Encoding]::UTF8)
 
 
📊 方案对比（碾压级优势）
 
方案 中文路径兼容性 执行速度 依赖要求 上手难度 
本项目.NET原生法 ✅ 完美兼容 ⚡ 最快 零依赖 极简 
PowerShell Get-Content ⚠️ 需指定编码 慢 无 中等 
CMD批处理 ❌ 天生缺陷 极慢 零依赖 复杂 
Python读取 ✅ 兼容 慢 需Python环境 中等 
C#编译程序 ✅ 兼容 极快 需编译 复杂 
 
📝 完整示例
 
powershell
  

# 读取桌面含"CC"关键词文件夹内的文件.md
$desktop = [Environment]::GetFolderPath("Desktop")
$folder = (Get-ChildItem $desktop -Directory | Where-Object { $_.Name -like "*CC*" }).FullName
$content = [System.IO.File]::ReadAllText("$folder\文件.md", [System.Text.Encoding]::UTF8)
Write-Host $content
 
 
🎯 适用场景
 
- OpenClaw等AI自动化工具的中文路径兼容修复
- Windows PowerShell脚本开发
- 批量处理中文命名的文件/文件夹
- 解决各类中文路径读取报错、乱码问题
 
📄 开源协议
 
MIT License
 
plaintext

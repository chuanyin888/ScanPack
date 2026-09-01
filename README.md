# ScanPack 扫码装箱打印工具

扫码装箱打印工具：用扫码枪扫描设备的 SN / MAC，自动配对成台，生成装箱标签（含 SN/MAC 条形码、二维码）并打印，同时自动导出 Excel 记录。

## 功能

- 扫码录入：SN / MAC 交替配对，智能识别 MAC 格式
- 扫码重复提示：重复的 SN/MAC 提示且不录入；勾选「测试模式」可忽略重复并录入
- 设备列表：最新扫的显示在最上面，支持单项删除、撤销、清空
- 打印数量：可设置打印份数（1~10 份）
- 打印标签：A4 版面，上半部分=装箱标签文字 + SN/MAC 二维码，下半部分=每台设备的 SN/MAC 条形码
- 打印预览：所见即所得（与打印效果一致），文字/二维码可拖拽调整位置并记忆
- 选择打印机：主页下拉框选择打印机（记忆），打印直接用该打印机
- Excel 导出：每次打印自动保存；保存位置可调、按日期自动建子文件夹、文件名用年月日时分
- 导入：从 CSV / Excel(.xlsx) 导入设备（SN/MAC），可追加或替换
- 联网更新：点「检查更新」检测新版，强制更新

## 使用

1. 双击 `ScanPack.exe`
2. 在「项目菜单」填型号/规格，「批次/日期」用日期选择器（默认当天，可改）
3. 用扫码枪扫入设备：每台先 SN 再 MAC，自动配对；新设备显示在列表顶部
4. 点「打印预览」看清排版（可拖拽文字/二维码调整并记住位置）
5. 选好「打印数量」和「打印机」，点「打印标签」即可打印并自动保存 Excel

> ⚠️ **重要**：`ScanPack.exe` 必须与同目录的 `zxing.dll`、`NPOI.dll`、`NPOI.OOXML.dll`、`NPOI.OpenXml4Net.dll`、`NPOI.OpenXmlFormats.dll`、`ICSharpCode.SharpZipLib.dll` 放在**同一个文件夹**才能运行（exe 依赖这些库，**不能只拷贝 exe**）。

## 目录结构

```
ScanPack.exe              主程序
zxing.dll                 二维码 / 条形码库
NPOI*.dll / SharpZipLib.dll  Excel 库
version.txt               更新清单（version + url）
```

## 发布 / 更新流程

每次发新版：

1. 改 `src\Updater.cs` 里的 `AppVersion`（如 `"2.0.0"` → `"2.0.1"`）
2. 重新编译出新的 `ScanPack.exe`
3. 在 GitHub 创建新的 Release（如 `v2.0.1`），上传新的 `ScanPack.exe`
4. 更新仓库根目录的 `version.txt`：
   ```
   version=2.0.1
   url=https://github.com/chuanyin888/ScanPack/releases/download/v2.0.1/ScanPack.exe
   ```
   （`version` 填新版本号，`url` 填 Release 附件下载地址）

完成以上 4 步后，用户点「检查更新」即可强制更新到最新版本。

## 版本历史

| 版本 | 说明 |
|------|------|
| v2.0.0 | 打印数量、导入功能、测试模式、重复提示、最新置顶、单项删除、日期选择器、选择打印机、强制更新、布局自适应、条形码规范、预览与打印一致等 |
| v1.0.1 | 强制更新 + TLS1.2 修复 |
| v1.0.0 | 首发版 |

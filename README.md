# Vim 技術分享簡報

這是一個使用 [Marp](https://marp.app/) 製作的 Vim 技術分享簡報。

## 內容來源

本簡報內容參考自以下網站：

2. [Guy Chien - Vim Basics](https://www.guychienll.dev/notes/vim/vim-basics)
3. [Guy Chien - VSCode 配置推薦](https://www.guychienll.dev/notes/vim/vscode)
4. [Guy Chien - JetBrains 配置推薦](https://www.guychienll.dev/notes/vim/jetbrains)

## 快速開始

### 方式一：使用 Marp CLI（推薦）

1. 安裝 Node.js（如果尚未安裝）

2. 安裝 Marp CLI：
```bash
npm install
```

3. 預覽簡報：
```bash
npm run preview
```

4. 匯出為 PDF：
```bash
npm run export:pdf
```

5. 匯出為 HTML：
```bash
npm run export:html
```

6. 匯出為 PPTX（PowerPoint）：
```bash
npm run export:pptx
```

### 方式二：使用 Marp for VS Code

1. 在 VS Code 中安裝 "Marp for VS Code" 擴充套件
2. 打開 `vim-sharing.md` 檔案
3. 按下 `Ctrl+Shift+P`（Mac: `Cmd+Shift+P`）
4. 輸入 "Marp: Open Preview" 來預覽簡報
5. 輸入 "Marp: Export Slide Deck" 來匯出簡報

### 方式三：線上編輯

訪問 [Marp Web](https://web.marp.app/) 並將 `vim-sharing.md` 的內容貼上即可。

## 簡報內容

本簡報包含以下主題：

1. Vim 簡介與歷史
2. 為何要學習 Vim
3. Vim 的三種模式
4. 基本操作
5. 編輯動作
6. 導航技巧
7. IDE 整合（VSCode & JetBrains）
8. 參考資料

## 客製化

您可以編輯 `vim-sharing.md` 檔案來自訂簡報內容。

### 修改主題

在檔案開頭的 YAML front matter 中修改主題：

```yaml
---
marp: true
theme: default  # 可選：default, gaia, uncover
paginate: true
backgroundColor: #fff
---
```

### 可用主題

- `default` - 預設主題
- `gaia` - 現代風格主題
- `uncover` - 簡約風格主題

## 專案結構

```
vim-sharing/
├── vim-sharing.md      # 簡報 Markdown 原始檔
├── README.md           # 本說明文件
└── package.json        # npm 設定檔
```

## 授權

本簡報內容參考自上述來源網站，僅供學習與分享使用。

## 參考資源

- [Marp 官方網站](https://marp.app/)
- [Marp CLI 文檔](https://github.com/marp-team/marp-cli)
- [Marp for VS Code](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode)

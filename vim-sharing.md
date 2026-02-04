---
marp: true
theme: default
paginate: true
backgroundColor: #ffffff
style: |
  section {
    font-size: 24px;
    padding: 50px;
  }
  h1 {
    color: #2c3e50;
    border-bottom: 3px solid #3498db;
    padding-bottom: 0.3em;
  }
  h2 {
    color: #34495e;
    margin-top: 1em;
  }
  h3 {
    color: #7f8c8d;
  }
  table {
    font-size: 20px;
    border-collapse: collapse;
  }
  code {
    background: #f4f4f4;
    padding: 2px 6px;
    border-radius: 3px;
    color: #e74c3c;
  }
  pre {
    background: #f8f8f8;
    color: #2c3e50;
    border: 1px solid #ddd;
    border-radius: 5px;
    padding: 1em;
  }
  strong {
    color: #e74c3c;
  }
---

<!-- _class: lead -->
# Vim 技術分享
## 高效的文本編輯器

*Guy Chien*

---

# 目錄

1. Vim 簡介
2. 為何學習 Vim
3. 三種模式
4. 基本操作
5. 編輯與導航
6. IDE 整合
7. 實用技巧

---

# Vim 簡介 - 歷史

- **Vi** (Visual) - Bill Joy, 1976
- **Vim** (Vi IMproved) - Bram Moolenaar, 1991
- Vim = Vi 的改進版本
- 發音：/vim/ (類似 "Jim")

---

# Vim 簡介 - 特點

- 所有 Unix-Like 系統內建
- 強大的程式編輯能力
- 語法高亮顯示
- 輕量且快速

---

# 為何學習 Vim？

## 普遍性 (Ubiquity)

- **系統內建** - 所有 Unix-Like 系統都有
- **無需安裝** - 隨時可用，不依賴外部工具
- **系統指令自動調用** - 如 `crontab`, `git` 等
- **遠端開發必備** - SSH 連線時的最佳選擇

## 效能 (Performance)

- **語法高亮** - 支援多種程式語言
- **大檔案處理快速** - 輕量級，開啟速度極快
- **鍵盤操作** - 減少手部移動，提升編輯速度

---

# 學習曲線

```
效率
 ^
 |            ___________
 |           |
 |           |
 |           |
 |___________|
 +------------------------> 時間
     投資期    →    回報期
```

**重點**：初期較困難，需刻意練習
度過學習期後，編輯效率將顯著提升

---

# 三種模式

| 模式 | 說明 |
|------|------|
| **Normal Mode** | 移動 (motion)、複製 (yank)、貼上 (paste)、刪除 (delete) |
| **Insert Mode** | 按 `i, o, a` 進入，輸入文字 |
| **Command Mode** | 按 `:, /, ?` 搜尋 (search)、取代 (replace)、存檔 (write) |

---

# 模式切換

```
    Normal Mode
         |
    `i`,`o`,`a`
         v
    Insert Mode
         |
       `ESC`
         v
    Normal Mode
         |
    `:`,`/`,`?`
         v
   Command Mode
```

---

# 啟動與離開

| 啟動 | 離開 |
|------|------|
| `vim file` | `:w` 存檔 (write) |
| | `:q` 離開 (quit) |
| | `:wq` 存檔後離開 (write & quit) |
| | `:q!` 強制離開 (force quit) |

---

# 游標移動 - 基礎

| 方向 | 指令 | 跳轉 | 指令 |
|------|------|------|------|
| 左 (left) | `h` | 行首 (home) | `0` |
| 下 (down) | `j` | 行尾 (end) | `$` |
| 上 (up) | `k` | 檔案開頭 (top) | `gg` |
| 右 (right) | `l` | 檔案結尾 (bottom) | `G` |

---

# 游標移動 - 進階

| 單字移動 | 指令 | 頁面移動 | 指令 |
|----------|------|----------|------|
| 下個字首 (word) | `w` | 下一頁 (forward) | `Ctrl+f` |
| 上個字首 (back) | `b` | 上一頁 (backward) | `Ctrl+b` |
| 字尾 (end) | `e` | 括號配對 (match) | `%` |

---

# 編輯動作

| 搭配 Text Object | 指令 | 獨立操作 | 指令 |
|-----------------|------|----------|------|
| 選擇 (visual) | `v` | 插入 (insert) | `i` |
| 複製 (yank) | `y` | 追加 (append) | `a` |
| 刪除 (delete) | `d` | 新行 (open) | `o` |
| 改變 (change) | `c` | 貼上 (paste) | `p` |

---

# 導航動作

| 基本指令 | 說明 | 進階指令 | 說明 |
|----------|------|----------|------|
| `f` | 找字元 (find) | `gd` | 前往定義 (go definition) |
| `w` | 下個字 (word) | `gg` | 檔案頂部 (go top) |
| `b` | 上個字 (back) | `G` | 檔案底部 (go bottom) |
| `/` | 搜尋 (search) | `{` `}` | 段落跳轉 (paragraph) |

---

# Text Object

## 組成：動作 + 範圍 + 名詞

| 動作 | 說明 | 範圍 | 說明 | 名詞 | 說明 |
|------|------|------|------|------|------|
| `v` | visual (選擇) | `i` | inner (內部) | `w` | word (單字) |
| `d` | delete (刪除) | `a` | around (包含) | `p` | paragraph (段落) |
| `y` | yank (複製) |  |  | `i` | indentation (縮排) |
| `c` | change (改變) |  |  | `t` | tag (標籤) |
|  |  |  |  | `(` `)` `{` `}` | 括號 |
|  |  |  |  | `'` `"` | 引號 |

---

# Text Object - 實例

```javascript
const message = "Hello Vim";
```

| 指令 | 說明 |
|------|------|
| `diw` | 刪除單字 (delete inner word) |
| `di"` | 刪除引號內容 (delete inner quote) |
| `daw` | 刪除單字含空白 (delete around word) |
| `ci(` | 改變括號內容 (change inner parenthesis) |
| `yap` | 複製段落 (yank around paragraph) |

---

# 搜尋與取代

| 搜尋 (search) | 取代 (substitute) |
|------|------|
| `/word` 向下搜尋 (forward) | `:s/old/new/` 當前行 (substitute) |
| `?word` 向上搜尋 (backward) | `:%s/old/new/g` 全文 (global) |
| `n` 下一個 (next) | `:%s/old/new/gc` 確認取代 (confirm) |
| `N` 上一個 (previous) | |

---

# 進階功能

## Visual Mode

- `v` - 字元選擇 (visual)
- `V` - 行選擇 (visual line)
- `Ctrl+v` - 區塊選擇 (visual block)

## 視窗管理 (window)

- `:split` - 水平分割 (horizontal split)
- `:vsplit` - 垂直分割 (vertical split)
- `:e filename` - 開啟檔案 (edit)

---

# VSCode 整合 - 安裝

## 插件

1. **Vim** (VSCodeVim)
2. Vim Easymotion (選用)

---

# VSCode 整合 - 設定

```json
{
  "vim.easymotion": true,
  "vim.incsearch": true,
  "vim.useSystemClipboard": true,
  "vim.hlsearch": true,
  "vim.leader": ";"
}
```

---

# VSCode 整合 - 快捷鍵

## 導航配置 (Navigation)

```json
{
  "vim.normalModeKeyBindingsNonRecursive": [
    {
      "before": ["z", "n"],
      "commands": ["editor.action.marker.next"]
    },
    {
      "before": ["z", "p"],
      "commands": ["editor.action.marker.prev"]
    }
  ]
}
```

---

# VSCode 整合 - 快捷鍵

## 重構配置 (Refactor - p42)

```json
{
  "vim.normalModeKeyBindingsNonRecursive": [
    {
      "before": ["R", "R"],
      "commands": ["p42.touchBar.refactor"]
    }
  ],
  "vim.visualModeKeyBindingsNonRecursive": [
    {
      "before": ["R", "R"],
      "commands": ["p42.touchBar.refactor"]
    }
  ]
}
```

---

# JetBrains 整合 - 安裝

## 插件

1. **IdeaVim** (必須)
2. AceJump (選用)
3. IdeaVim-EasyMotion (選用)

---

# JetBrains 整合 - 設定

```vim
let mapleader=';'

set number
set clipboard+=unnamed
set hlsearch
set incsearch
set easymotion
set surround
```

---

# JetBrains 整合 - Action

```vim
map RR :action Refactorings.QuickListPopupAction<CR>
map RN :action RenameElement<CR>
map RI :action Inline<CR>
map RV :action IntroduceVariable<CR>
```

提示：輸入 `:actionlist` 查看所有可用 action

---

# 實用技巧 - 整行操作

| 操作 | 指令 | 縮排 (indent) | 指令 |
|------|------|------|------|
| 刪除整行 (delete line) | `dd` | 增加縮排 (shift right) | `>>` |
| 複製整行 (yank line) | `yy` | 減少縮排 (shift left) | `<<` |
| 改變整行 (change line) | `cc` | | |
| 重複動作 (repeat) | `.` |  |  |

---

# 實用技巧 - 組合技

| 刪除組合 (delete) | 複製組合 (yank) |
|----------|----------|
| `ciw` 改變單字 (change inner word) | `yap` 複製段落 (yank around paragraph) |
| `di(` 刪除括號內容 (delete inner paren) | `yi"` 複製引號內容 (yank inner quote) |
| `dG` 刪除到檔尾 (delete to end) | `yy` 複製整行 (yank line) |
| `d$` 刪除到行尾 (delete to line end) | `y$` 複製到行尾 (yank to line end) |

---

# Vim 設定檔

```vim
" 基本設定
set number
syntax on

" 搜尋設定
set hlsearch
set incsearch
set ignorecase
set smartcase
```

---

# Vim 設定檔

```vim
" 縮排設定
set expandtab
set tabstop=4
set shiftwidth=4
set autoindent

" 其他設定
set showcmd
set ruler
```

---

# 學習資源

## 學習步驟

1. 執行 `vimtutor`
2. 每日學一個新指令
3. 整合至 IDE

## 練習網站

- [Vim Adventures](https://vim-adventures.com/)
- [Vim Golf](https://www.vimgolf.com/)

---

# 常見問題

**Q: 如何退出 Vim？**
A: 按 `ESC` 後輸入 `:q` 或 `:wq`

**Q: Vim 太難學？**
A: 從基本操作開始，每天學習一點

**Q: 需要放棄滑鼠？**
A: 不需要，可以逐步過渡

---

# Vim CheatSheet

![width:800px](https://pbs.twimg.com/media/DOSNfezU8AIzrpF.jpg)

---

<!-- _class: lead -->

# Thank You!
## Q & A

學習 Vim，提升編輯效率

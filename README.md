<h1 align="center">
🌈 NeoColumn.nvim
</h1>

<p align="center">
  <a href="http://www.lua.org">
    <img
      alt="Lua"
      src="https://img.shields.io/badge/Lua-blue.svg?style=for-the-badge&logo=lua"
    />
  </a>
  <a href="https://neovim.io/">
    <img
      alt="Neovim"
      src="https://img.shields.io/badge/NeoVim-%2357A143.svg?&style=for-the-badge&logo=neovim&logoColor=white"
    />
  </a>
</p>

![demo](https://raw.githubusercontent.com/ecthelionvi/Images/main/NeoColumn.gif)

## 📢 Introduction

NeoColumn is a Neovim plugin that shows a focused ColorColumn at a specific position to manage line length. It highlights individual characters, minimizing clutter and enhancing readability

## ✨ Features

- Display a focused ColorColumn at the desired position
- Exclude specified filetypes from the ColorColumn 
- Toggle NeoColumn on and off
- Customizable colors 

## 💾 Persistence

NeoColumn maintains the ColorColumn settings for each file, including visibility and position, across sessions.

## 🛠️ Usage

To toggle NeoColumn on/off, you can use the `ToggleNeoColumn` command:

```vim
:ToggleNeoColumn
```
You can also create a keybinding to toggle NeoColumn more conveniently:

```lua
vim.keymap.set("n", "<leader>h", "<cmd>ToggleNeoColumn<cr>", { noremap = true, silent = true })
```

To clear the list of enabled/disabled files in NeoColumn, you can use the `ClearNeoColumn` command:

```vim
:ClearNeoColumn
```

## 📦 Installation

1. Install via your favorite package manager.

- [lazy.nvim](https://github.com/folke/lazy.nvim)
```Lua
{
  "ecthelionvi/NeoColumn.nvim",
  opts = {}
},
```

- [packer.nvim](https://github.com/wbthomason/packer.nvim)
```Lua
use "ecthelionvi/NeoColumn.nvim"
```

2. Setup the plugin in your `init.lua`. This step is not needed with lazy.nvim if `opts` is set as above.
```Lua
require("NeoColumn").setup()
```

## 🔧 Configuration

You can pass your config table into the `setup()` function or `opts` if you use lazy.nvim.

The available options:

- `fg_color`(string) : foreground color of the ColorColumn as a hex code (e.g., `"#FF0000"`)  
  - `""` (default, falls back to the foreground color of the `IncSearch` highlight group)
- `bg_color`(string) : background color of the ColorColumn as a hex code (e.g., `"#00FF00"`)
  - `""` (default, falls back to the background color of the `IncSearch` highlight group)
- `NeoColumn` (string / table) : character position at which the ColorColumn/s appears
  - `"80"` (default)
  - `{ "80", "100" }` 
- `always_on` (boolean) : switch on/off the ColorColumn by default  
  - `false` (default)
- `custom_NeoColumn` (table) : custom ColorColumn values for specific filetypes   
  - `false` (default)
- `excluded_ft` (table) : filetypes to exclude from the ColorColumn  
  - `{}` (default)

### Default Config

```Lua
local config = {
  fg_color = '',
  bg_color = '',
  NeoColumn = '80',
  always_on = false,
  custom_NeoColumn = {},
  excluded_ft = { "text", "markdown" },
}
```

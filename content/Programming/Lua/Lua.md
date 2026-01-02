**Lua** is a lightweight, high-level, multi-paradigm programming language designed primarily for embedded use in applications. It is the configuration language for Neovim. 

https://www.lua.org/docs.html

---
#### Core Concepts in Neovim Config

**1. Tables**
Only data structure is the **Table**. It acts as a [[Hash Table(s)]]

```lua
-- List (Array-like)
local plugins = { "nvim-lspconfig", "nvim-cmp" }

-- Dictionary (Map-like)
local options = {
    ensure_installed = { "c", "lua" },
    auto_install = true,
}
```
- **Usage:** Used everywhere in `lazy.nvim` specs to define plugin names and their options.

**2. Modules & Require**
Lua encourages splitting code into separate files.
- `require("module_name")`: Loads and runs a Lua file from the `lua/` directory.
- `return`: A file typically returns a table or function that `require` captures.

```lua
-- In init.lua
require("settings") -- Runs lua/settings.lua
```

**3. The Vim API (`vim`)**
Neovim exposes a global `vim` table to interact with the editor.
- `vim.opt`: Sets editor options (e.g., `vim.opt.relativenumber = true`).
- `vim.keymap.set`: Defines keybindings.
- `vim.fn`: Calls legacy Vimscript functions.
- `vim.api`: Accesses the low-level API (buffers, windows).

---
#### Key Syntax
- **Variables:** `local x = 10` (Always use `local` to avoid polluting the global namespace).
- **Comments:** `-- This is a comment`.
- **Strings:** `"` or `'` are interchangeable.

---

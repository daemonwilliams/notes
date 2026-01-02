**Neovim Diagnostics** is the configuration of the built-in LSP client to display **errors**, **warnings**, and **hints** directly in the editor buffer.

---
#### Navigation Keymaps
Efficiently move between diagnostics within the current buffer:

- `[d` : Jump to the **previous** diagnostic.
- `]d` : Jump to the **next** diagnostic.
- `<leader>e` : Open the diagnostic message in a **floating window** (useful for long messages truncated by virtual text).
- `<leader>q` : Open all diagnostics for the current buffer in the **Location List**.

---
#### Project-Wide Diagnostics
Search and filter diagnostics across the entire project using Telescope:

- `<leader>pd` : Opens **Telescope Diagnostics**, allowing fuzzy searching through all project errors and warnings.

---
#### Configuration Files
- **LSP Settings:** `lua/lazy_packages/lsp.lua` (Defines signs, virtual text, and buffer navigation).
- **Telescope Mappings:** `lua/lazy_packages/telescope.lua` (Defines `<leader>pd`).
- **Global Options:** `lua/settings.lua` (Ensures `signcolumn` is enabled).

[[Neovim Config]]

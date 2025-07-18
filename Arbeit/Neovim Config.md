```
vim.keymap.set("n", "<F2>", ":NERDTreeToggle<CR>")          -- Toggle file explorer with F2
vim.keymap.set("n", "<F8>", ":set relativenumber!<CR>")     -- Toggle relative line numbers
vim.keymap.set("n", "<leader>v", ":vsplit %<CR>")           -- Vertical split with current file
vim.keymap.set("n", "<C-s>", ":w<CR>")                      -- Save with Ctrl+S
vim.keymap.set("n", "\\", ":nohlsearch<CR>")                -- Clear search highlights

```
### Spliting
- in nerdTree 
	- o to open normally
	- i in horizontal split
	- s in vertical split
	- t in different tab
### Moving in splits.
- option H
- option J
- option K
- option L

### Tab moving
```
vim.keymap.set("n", "<Tab>", ":tabnext<CR>")
vim.keymap.set("n", "<S-Tab>", ":tabprevious<CR>")
vim.keymap.set("n", "<leader>tn", ":tabnew<CR>")
vim.keymap.set("n", "<leader>tc", ":tabclose<CR>")
vim.keymap.set("n", "<leader>to", ":tabonly<CR>")
```

| Keys          | Action                   |
| ------------- | ------------------------ |
| `<Tab>`       | Next tab                 |
| `<Shift-Tab>` | Previous tab             |
| `<Space>tn`   | New tab                  |
| `<Space>tc`   | Close current tab        |
| `<Space>to`   | Close all **other** tabs |

--- 
Here is the complete init.lua file

```lua
-- ========== BASIC SETTINGS ==========
vim.opt.number = true
vim.opt.relativenumber = true
vim.opt.tabstop = 4
vim.opt.shiftwidth = 4
vim.opt.expandtab = true
vim.opt.smartindent = true
vim.opt.autoindent = true
vim.opt.scrolloff = 8
vim.opt.termguicolors = true
vim.opt.clipboard = "unnamedplus"
vim.opt.mouse = "a"
vim.opt.encoding = "utf-8"
vim.opt.backup = false
vim.opt.writebackup = false
vim.opt.showtabline = 2
vim.opt.swapfile = false
vim.opt.hlsearch = true
vim.opt.incsearch = true
vim.g.mapleader = " "

-- ========== PLUGIN MANAGER ==========
-- Install lazy.nvim if it's not already installed
local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not vim.loop.fs_stat(lazypath) then
  vim.fn.system({
    "git", "clone", "--filter=blob:none",
    "https://github.com/folke/lazy.nvim.git", lazypath
  })
end
vim.opt.rtp:prepend(lazypath)

-- ========== PLUGINS ==========
require("lazy").setup({
  -- Colorscheme
  { "nyoom-engineering/oxocarbon.nvim" },

  -- File explorer
  { "preservim/nerdtree" },

  -- Auto pairs
  { "jiangmiao/auto-pairs" },

  -- C++ syntax enhancements
  { "octol/vim-cpp-enhanced-highlight" },

  -- Statusline
  { "nvim-lualine/lualine.nvim" },

  -- Tabline plugin
  { "akinsho/bufferline.nvim", dependencies = { "nvim-tree/nvim-web-devicons" } },

  -- Fuzzy finder
  { "nvim-telescope/telescope.nvim", tag = '0.1.5', dependencies = { 'nvim-lua/plenary.nvim' } },
})

-- ========== COLORSCHEME ==========
vim.cmd("colorscheme oxocarbon")

-- ========== STATUSLINE ==========
require("lualine").setup {
  options = { theme = "auto" }
}

-- ========== KEYMAPS ==========
vim.keymap.set("n", "<F2>", ":NERDTreeToggle<CR>")
vim.keymap.set("n", "<F8>", ":set relativenumber!<CR>")
vim.keymap.set("n", "<leader>v", ":vsplit %<CR>")
vim.keymap.set("n", "<C-s>", ":w<CR>")
vim.keymap.set("n", "\\", ":nohlsearch<CR>")

vim.keymap.set('n', '<A-h>', '<C-w>h')
vim.keymap.set('n', '<A-l>', '<C-w>l')
vim.keymap.set('n', '<A-k>', '<C-w>k')
vim.keymap.set('n', '<A-j>', '<C-w>j')
--
-- Tab navigation
vim.keymap.set("n", "<Tab>", ":tabnext<CR>")
vim.keymap.set("n", "<S-Tab>", ":tabprevious<CR>")
vim.keymap.set("n", "<leader>tn", ":tabnew<CR>")
vim.keymap.set("n", "<leader>tc", ":tabclose<CR>")
vim.keymap.set("n", "<leader>to", ":tabonly<CR>")
-- ========== CPP COMPILE/RUN ==========
vim.api.nvim_create_autocmd("FileType", {
  pattern = "cpp",
  callback = function()
    vim.keymap.set("n", "<F9>",
      ":w<CR>:!g++ -std=c++17 -Wall -Wextra -O2 % -o %< && time ./%<<CR>",
      { buffer = true })
  end
})



```
# tailwind-highlight.nvim

![License](https://img.shields.io/badge/license-GPL2-brightgreen?style=flat)
![Version](https://img.shields.io/github/v/release/princejoogie/tailwind-highlight.nvim?color=%2349C31B)

Highlight [Tailwind CSS](https://tailwindcss.com/) classes in [neovim](https://neovim.io/)

> "The neovim plugin [used](https://github.com/bautistaaa/dotfiles/blob/d53f8d0fe4b226e90bcbfcecc8ceea6a270ccd1c/nvim/lua/trash/plugins.lua#L65) by a Netflix Engineer (@trashh_dev) and Amazon engineer @Hacksore"

![tailwind-highlight-demo](./assets/demo.png)

## Installation

- **[Packer](https://github.com/wbthomason/packer.nvim)**

  ```lua
  -- required dependency
  use "neovim/nvim-lspconfig"
  -- (optional) for installing tailwindcss language server
  use "williamboman/nvim-lsp-installer"

  use "princejoogie/tailwind-highlight.nvim"
  ```

- **[Vim Plug](https://github.com/junegunn/vim-plug)**

  ```vim
  " required dependency
  Plug 'neovim/nvim-lspconfig'
  " (optional) for installing tailwindcss language server
  Plug 'williamboman/nvim-lsp-installer'

  Plug 'princejoogie/tailwind-highlight.nvim'
  ```

## Usage

```lua
local tw_highlight = require('tailwind-highlight')
```

### Without Lsp Installer

> Manually install [tailwindcss-language-server](https://www.npmjs.com/package/@tailwindcss/language-server)

```lua
require('lspconfig').tailwindcss.setup({
  on_attach = function(client, bufnr)
    -- rest of you config
    tw_highlight.setup(client, bufnr, {
      single_column = false,
      mode = 'background',
      debounce = 200,
    })
  end
})
```

### With Lsp Installer

> `:LspInstall tailwindcss`

```lua

require('nvim-lsp-installer').on_server_ready(function(server)
  local opts = {
    on_attach = function(client, bufnr)
      -- rest of you config
      tw_highlight.setup(client, bufnr, {
        single_column = false,
        mode = 'background',
        debounce = 200,
      })
    end
  }

  server:setup(opts)
end)
```

### Methods

| Method  | Args                    | Returns  |
| ------- | ----------------------- | -------- |
| `setup` | `(client, bufnr, opts)` | `void`   |
| `ping`  | `N/A`                   | `string` |

### Setup Options

| Option          | Description                               |      Default |
| --------------- | ----------------------------------------- | -----------: |
| `single_column` | highlight only first character            |      `false` |
| `mode`          | highlight mode `foreground \| background` | `background` |
| `debounce`      | delay on updating highlights (ms)         |        `200` |

---

Like the project? would appreciate a coffee ☕

[![Buy Me A Coffee](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/princejoogie)

### Contributor list

[![Contributors](https://contrib.rocks/image?repo=princejoogie/tailwind-highlight.nvim)](https://github.com/princejoogie/tailwind-highlight.nvim/graphs/contributors)

---

Made with ☕ by [Prince Carlo Juguilon][portfolio]

[portfolio]: https://princecaarlo.tech/
[github]: https://github.com/princejoogie/
[twitter]: https://twitter.com/princecaarlo/
[instagram]: https://www.instagram.com/princecaarlo/
[linkedin]: https://www.linkedin.com/in/princejoogie/

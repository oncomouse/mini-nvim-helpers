# Custom helpers for [mini.nvim](https://github.com/echasnovski/mini.nvim)

This module packages two helpers I use frequently in my Neovim configuration: `disable_mini_module` and `configure_mini_module`.

Both automate some of the repetitive tasks mini.nvim asks.

Here are some usage examples:

```
require("mini.helpers").disable_mini_module("indentscope", {
    terminal = true,
    filetype = { "help", "alpha", "dashboard", "neo-tree", "Trouble", "lazy", "mason" },
    buftype = { "quickfix" },
})

```

The above disables mini.indentscope in terminal, quickfix buffers, and a number of filetypes.

```
require("mini.helpers").configure_mini_module("ai", {
    custom_textobjects = {
        ["*"] = spec_pair("*", "*", { type = "greedy" }), -- Grab all asterisks when selecting
        ["_"] = spec_pair("_", "_", { type = "greedy" }), -- Grab all underscores when selecting
        ["l"] = { "%b[]%b()", "^%[().-()%]%([^)]+%)$" }, -- Link targeting name
        ["L"] = { "%b[]%b()", "^%[.-%]%(()[^)]+()%)$" }, -- Link targeting href
    },
}, {
    filetype = "markdown",
})
```

This second example configures a number of custom textobjects for markdown buffers using mini.ai

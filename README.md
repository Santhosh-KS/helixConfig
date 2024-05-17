# My helix config.toml file

*PATH:* `~/.config/helix/config.toml
```toml
# Theme related settings
# theme = 'dracula'
theme = 'dark_plus'

# editor related settings
[editor]
line-number = 'relative'
mouse = false
bufferline = "multiple"
shell = ["sh", "-c"]
auto-completion = true
auto-format = true
text-width = 80
default-line-ending = "native"

[editor.cursor-shape] 
insert = "bar"

[editor.statusline]
left = ["mode", "spinner"]
center = ["file-name"]
right = ["diagnostics", "selections", "position", "file-encoding", "file-line-ending", "file-type"]
separator = "│"
mode.normal = "NORMAL"
mode.insert = "INSERT"
mode.select = "SELECT"

[editor.auto-pairs]
'(' = ')'
'{' = '}'
'[' = ']'
'"' = '"'
'`' = '`'
'<' = '>'

# or control each character
[editor.whitespace.render]
space = "all"
tab = "all"
nbsp = "none"
nnbsp = "none"
newline = "none"

[editor.whitespace.characters]
space = "·"
nbsp = "⍽"
nnbsp = "␣"
tab = "»"
newline = "⏎"
tabpad = "»" # Tabs will look like "» ··" (depending on tab width)


[editor.indent-guides]
render = true
character = "▏" # Some characters that work well: "▏", "┆", "┊", "⸽"
skip-levels = 1

[editor.gutters]
layout = ["diff", "diagnostics", "line-numbers", "spacer"]
[editor.gutters.line-numbers]
min-width = 2

# Keymappings related settings
[keys.normal]
esc = ["collapse_selection", "keep_primary_selection"]
S-h = ":buffer-next"
S-l = ":buffer-previous"
# Some of the vim related key bindinos which I'm used to
# x = "delete_char_forward"

[keys.normal.Z]
Z = ":wq"
# j = "scroll_up"
# k = "scroll_down"

[keys.normal.G]
G= "goto_file_end"

# create a new minor mode bound to `+``
# [keys.normal."+"]
# m = ":run-shell-command make"
# c = ":run-shell-command caroo build"
# t = ":run-shell-command cargo test"

```

# LSP settings   

*PATH:* `~/.config/helix/languages.toml`

```toml
# If you edit the use-grammer field please run  the below "fetch" and "build" commands 
# hx --grammar fetch and hx --grammar build
use-grammars = { only = [ "rust", "c", "cpp", "swift", "elm", "js", "html", "typescript","yaml", "json", "toml", "docker" ] }

[[language]]
name = "swift"
scope = "source.swift"
injection-regex = "swift"
file-types = ["swift", "SWIFT"]
# comment-tokens = ["///", "//"]
block-comment-tokens = { start = "/**", end = "**/"}
indent = { tab-width = 2, unit = "  " }
formatter = {command = "swift-format", args = ["format -i -r -p Sources/ Tests/"]}
language-servers = [ "sourcekit-lsp" ]
auto-format = true
language-id = "swift"
roots = ["Package.swift",  "Package.resolved", ".git", "Sources", "Tests"]

# https://cs.opensource.google/go/x/tools/+/refs/tags/gopls/v0.15.3:gopls/doc/helix.md
[language-server.gopls]
command = "gopls"
args = ["-logfile=/tmp/gopls.log",  "serve"]
[language-server.gopls.config]
"ui.diagnostic.staticcheck" = true

```

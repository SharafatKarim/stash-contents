---
Owner: Sharafat Karim
Last edited time: 2023-01-08T09:19
---
[https://github.com/echuraev/keyboard_layout](https://github.com/echuraev/keyboard_layout)

---

in the awesome rc.lua,

```Lua
-- keyboard layout
local keyboard_layout = require("keyboard_layout")

local kbdcfg = keyboard_layout.kbdcfg({type = "tui"})

kbdcfg.add_primary_layout("English", "US", "us")
kbdcfg.add_primary_layout("Bangla", "BD", "bd")
kbdcfg.bind()

-- local kbdcfg = keyboard_layout.kbdcfg({type = "gui"})
--
-- kbdcfg.add_primary_layout("English", "US", "us")
-- kbdcfg.add_primary_layout("Bangla", "BD", "bd")
-- kbdcfg.bind()
```

line (9-14) are commented
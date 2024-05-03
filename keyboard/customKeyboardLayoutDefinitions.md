Custom keyboard layout definitions
===

[TOC]

### Check keyboard layout

```bash
$ setxkbmap -print
xkb_keymap {
	xkb_keycodes  { include "evdev+aliases(qwerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+us+inet(evdev)"	};
	xkb_geometry  { include "pc(pc105)"	};
};
```

### Backup file

```bash
$ sudo cp /usr/share/X11/xkb/symbols/us /usr/share/X11/xkb/symbols/us.bak
$ sudo cp /usr/share/X11/xkb/symbols/us /usr/share/X11/xkb/symbols/us.bak
```

### Modify layout what you want

Note:
1. `Mode_switch` does not work for me, so I use `ISO_Level3_Shift` to switch to Mod5.
2. This is only works in Xorg session, It doesn't in Wayland session for me.

```bash
$ sudo vim /usr/share/X11/xkb/symbols/pc
key <CAPS> {    [ Caps_Lock  ]   }; ==> key <CAPS> {    [ ISO_Level3_Shift  ]   };
---
 // Fake keys for virtual<->real modifiers mapping:
 key <LVL3> {    [ ISO_Level3_Shift  ]   };
 key <MDSW> {    [ Mode_switch       ]   };
 modifier_map Mod5   { <LVL3>, <MDSW> };
```

```bash
$ sudo vim /usr/share/X11/xkb/symbols/us
default  partial alphanumeric_keys modifier_keys                                                                                 
xkb_symbols "basic" {

    name[Group1]= "English (US)";

    key <TLDE> {    [     grave,    asciitilde, Caps_Lock   ]   };   
    key <AE01> {    [     1,    exclam      ]   };   
    key <AE02> {    [     2,    at      ]   };   
    key <AE03> {    [     3,    numbersign  ]   };   
    key <AE04> {    [     4,    dollar      ]   };   
    key <AE05> {    [     5,    percent     ]   };   
    key <AE06> {    [     6,    asciicircum ]   };   
    key <AE07> {    [     7,    ampersand   ]   };   
    key <AE08> {    [     8,    asterisk    ]   };   
    key <AE09> {    [     9,    parenleft   ]   };   
    key <AE10> {    [     0,    parenright  ]   };   
    key <AE11> {    [     minus,    underscore  ]   };   
    key <AE12> {    [     equal,    plus        ]   };   

    key <AD01> {    [     q,    Q,  Home    ]   };   
    key <AD02> {    [     w,    W,  Up      ]   };   
    key <AD03> {    [     e,    E,  End     ]   };   
    key <AD04> {    [     r,    R,  Prior   ]   };   
    key <AD05> {    [     t,    T,  Escape  ]   };   
    key <AD06> {    [     y,    Y,  Delete  ]   };   
    key <AD07> {    [     u,    U,  Home    ]   };   
    key <AD08> {    [     i,    I,  Up      ]   };   
    key <AD09> {    [     o,    O,  End     ]   };   
    key <AD10> {    [     p,    P,  Print   ]   };   
    key <AD11> {    [ bracketleft,  braceleft   ]   };   
    key <AD12> {    [ bracketright, braceright  ]   };   

    key <AC01> {    [     a,    A,  Left        ]   };   
    key <AC02> {    [     s,    S,  Down        ]   };   
    key <AC03> {    [     d,    D,  Right       ]   };   
    key <AC04> {    [     f,    F,  Next        ]   };   
    key <AC05> {    [     g,    G,  Insert      ]   };   
    key <AC06> {    [     h,    H,  BackSpace   ]   };   
    key <AC07> {    [     j,    J,  Left        ]   };   
    key <AC08> {    [     k,    K,  Down        ]   };   
    key <AC09> {    [     l,    L,  Right       ]   };   
    key <AC10> {    [ semicolon,    colon       ]   };   
    key <AC11> {    [ apostrophe,   quotedbl    ]   };   

```

### Logout and login again

### Reference

> * https://help.ubuntu.com/community/Custom%20keyboard%20layout%20definitions
> * https://github.com/Chunlin-Li/Chunlin-Li.github.io/blob/master/blogs/linux/ubuntu-xkb-keyboard-remap.md
> * https://askubuntu.com/questions/1040642/how-to-stop-gnome-from-overriding-xkb-layout

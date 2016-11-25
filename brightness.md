## Brightness adjust

### xbacklight

Brightness can be set using the `xorg-xbacklight` package.
`sudo pacman -S  xorg-xbacklight`

>**Note:**
>xbacklight only works with intel. Radeon does not support the RandR backlight property.

for example to increase or decrease brightness by 10%:
```bash
xbacklight -inc 10
xbacklight -dec 10
```

These commands can be bound to keyboard keys as described in `Extra keyboard keys in Xorg`, like `xbindkeys`.

##### install and configure `xbindkeys`:
`sudo pacman -S xbindkeys`

Create a file named `.xbindkeysrc` in your home directory:
`$ touch ~/.xbindkeysrc`

Alternatively, you can create a sample file (Note this includes some bindings such as `Ctrl+f`, which you may want to edit or remove):
`$ xbindkeys -d > ~/.xbindkeysrc`

Now you can either edit `~/.xbindkeysrc` to set keybindings.
>**Tip:** After you made a change, execute `xbindkeys -p` to reload the configuration file and apply the changes.

##### Identifying keycodes
To find the keycodes for a particular key, enter the following command:
`$ xbindkeys -k`
A blank window will pop up. Press the key(s) to which you wish to assign a command and *xbindkeys* will output a handy snippet that can be entered into `~/.xbindkeysrc`. For example, while the blank window is open, press `Alt+o` to get the following output (results may vary):
```bash
"(Scheme function)"
    m:0x8 + c:32
    Alt + o
```
The first line represents a command. The second contains the state (0x8) and keycode (32) as reported by `xev`. The third line contains the keysyms associated with the given keycodes. To use this output, copy either one of the last two lines to `~/.xbindkeysrc` and replace "(Scheme function)" with the command you wish to perform.

**in my case, to bind keys to adjust the backlight, edit `~/.xbindkeysrc` like below:**
```bash
# increase backlight by 10
"xbacklight -inc 10"
m:0x5 + c:35
# Control+Shift + bracketright

# decrease backlight by 10
"xbacklight -dec 10"
m:0x5 + c:34
#Control+Shift + bracketleft
```

#### automatically run xbindkeys on startup

`＃ vim /etc/rc.local`

add below command:

`/usr/bin/xbindkeys`

save and quit.
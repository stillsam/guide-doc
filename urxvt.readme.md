## `~/.Xresources`


#### add content below.

>(not sure) *If want to set urxvt as default terminal, Setting from command-line without keyboard choice:*
> `sudo update-alternatives --set x-terminal-emulator /usr/bin/urxvt`

##### make change effective:
`xrdb ~/.Xresources`

复制 就是直接选定

黏贴就是鼠标中键

从非urxvt复制并黏贴入urxvt用shitf+insert

***
```bash
! Compile xft: Attempt to find a visual with the given bit depth; option -depth.
! URxvt*depth: bitdepth

! Compile xft: Turn on/off double-buffering for xft (default enabled).  On some card/driver combination enabling it
! URxvt*buffered: boolean

! Create the window with the specified X window geometry [default 80x24]; option -geometry.
! URxvt*geometry: geom

! Use the specified colour as the windows background colour [default White]; option -bg.
URxvt*background: #2b2b2b

! Use the specified colour as the windows foreground colour [default Black]; option -fg.
URxvt*foreground: #dedede

! Use the specified colour for the colour value n, where 0-7 corresponds to low-intensity (normal) colours and 8-15
! URxvt*colorn: colour

! black
URxvt*color0  : #2E3436
URxvt*color8  : #555753
! red
URxvt*color1  : #CC0000
URxvt*color9  : #EF2929
! green
URxvt*color2  : #4E9A06
URxvt*color10 : #8AE234
! yellow
URxvt*color3  : #C4A000
URxvt*color11 : #FCE94F
! blue
URxvt*color4  : #3465A4
URxvt*color12 : #729FCF
! magenta
URxvt*color5  : #75507B
URxvt*color13 : #AD7FA8
! cyan
URxvt*color6  : #06989A
URxvt*color14 : #34E2E2
! white
URxvt*color7  : #D3D7CF
URxvt*color15 : #EEEEEC

!
! URxvt*colorBD: colour

! Use the specified colour to display bold or italic characters when the foreground colour is the default. If font styles
! URxvt*colorIT: colour

! Use the specified colour to display underlined characters when the foreground colour is the default.
! URxvt*colorUL: colour

! If set, use the specified colour as the colour for the underline itself. If unset, use the foreground colour.
! URxvt*underlineColor: colour

! If set, use the specified colour as the background for highlighted characters. If unset, use reverse video.
! URxvt*highlightColor: colour

! If set and highlightColor is set, use the specified colour as the foreground for highlighted characters.
! URxvt*highlightTextColor: colour

! Use the specified colour for the cursor. The default is to use the foreground colour; option -cr.
! URxvt*cursorColor: colour

! Use the specified colour for the colour of the cursor text. For this to take effect, cursorColor must also be specified.
! URxvt*cursorColor2: colour

! True: simulate reverse video by foreground and background colours; option -rv. False: regular screen colours [default];
! URxvt*reverseVideo: boolean

! True: specify that jump scrolling should be used. When receiving lots of lines, urxvt will only scroll once a whole
! URxvt*jumpScroll: boolean

! True: (the default) specify that skip scrolling should be used. When receiving lots of lines, urxvt will only scroll once
! URxvt*skipScroll: boolean

! Fade the text by the given percentage when focus is lost; option -fade.
! URxvt*fading: number

! Fade to this colour, when fading is used (see fading:). The default colour is black; option -fadecolor.
! URxvt*fadeColor: colour

! Set the application icon pixmap; option -icon.
! URxvt*iconFile: file

! Use the specified colour for the scrollbar [default #B2B2B2].
! URxvt*scrollColor: colour

! Use the specified colour for the scrollbars trough area [default #969696]. Only relevant for rxvt (non XTerm/NeXT)
! URxvt*troughColor: colour

! The colour of the border around the text area and between the scrollbar and the text.
! URxvt*borderColor: colour

! Select the fonts to be used. This is a comma separated list of font names that are checked in order when trying to find
URxvt*font: xft:DejaVu Sans Mono:pixelsize=13

URxvt*boldFont: xft:DejaVu Sans Mono:pixelsize=13:style=Bold

!
! URxvt*italicFont: fontlist

! The font list to use for displaying bold, italic or bold italic characters, respectively.
! URxvt*boldItalicFont: fontlist

! When font styles are not enabled, or this option is enabled (True, option -is, the default), bold/blink font styles imply
! URxvt*intensityStyles: boolean

! Set window title string, the default title is the command-line specified after the -e option, if any, otherwise the
! URxvt*title: string

! Set the name used to label the windows icon or displayed in an icon manager window, it also sets the windows title
! URxvt*iconName: string

! True: de-iconify (map) on receipt of a bell character. False: no de-iconify (map) on receipt of a bell character
! URxvt*mapAlert: boolean

! True: set the urgency hint for the wm on receipt of a bell character.  False: do not set the urgency hint [default].
! URxvt*urgentOnBell: boolean

! True: use visual bell on receipt of a bell character; option -vb.  False: no visual bell [default]; option +vb.
! URxvt*visualBell: boolean

! True: start as a login shell by prepending a - to argv[0] of the shell; option -ls. False: start as a normal sub-shell
! URxvt*loginShell: boolean

! Specify the maximum time in milliseconds between multi-click select events. The default is 500 milliseconds; option -mc.
! URxvt*multiClickTime: number

! True: inhibit writing record into the system log file utmp; option -ut. False: write record into the system log file utmp
! URxvt*utmpInhibit: boolean

! Specify a command pipe for vt100 printer [default lpr(1)]. Use Print to initiate a screen dump to the printer and Ctrl-
! URxvt*print-pipe: string

! Set scrollbar style to rxvt, plain, next or xterm. plain is the authors favourite.
! URxvt*scrollstyle: mode

! Set the scrollbar width in pixels.
! URxvt*thickness: number

! True: enable the scrollbar [default]; option -sb. False: disable the scrollbar; option +sb.
URxvt*scrollBar: false

! True: place the scrollbar on the right of the window; option -sr.  False: place the scrollbar on the left of the window;
! URxvt*scrollBar_right: boolean

! True: display an rxvt scrollbar without a trough; option -st.  False: display an rxvt scrollbar with a trough; option
! URxvt*scrollBar_floating: boolean

! Align the top, bottom or centre [default] of the scrollbar thumb with the pointer on middle button press/drag.
! URxvt*scrollBar_align: mode

! True: scroll to bottom when tty receives output; option -si.  False: do not scroll to bottom when tty receives output;
! URxvt*scrollTtyOutput: boolean

! True: scroll with scrollback buffer when tty receives new lines (i.e.  try to show the same lines) and scrollTtyOutput is
! URxvt*scrollWithBuffer: boolean

! True: scroll to bottom when a non-special key is pressed. Special keys are those which are intercepted by rxvt-unicode
! URxvt*scrollTtyKeypress: boolean

! Save number lines in the scrollback buffer [default 64]. This resource is limited on most machines to 65535; option -sl.
! URxvt*saveLines: number

! Internal border of number pixels. This resource is limited to 100; option -b.
! URxvt*internalBorder: number

! External border of number pixels. This resource is limited to 100; option -w, -bw, -borderwidth.
! URxvt*externalBorder: number

! Set MWM hints to request a borderless window, i.e. if honoured by the WM, the rxvt-unicode window will not have window
! URxvt*borderLess: boolean

! Compile frills: Disable the usage of the built-in block graphics/line drawing characters and just rely on what the
! URxvt*skipBuiltinGlyphs: boolean

! Specifies the terminal type name to be set in the TERM environment variable; option -tn.
! URxvt*termName: termname

! Specifies number of lines (pixel height) to insert between each row of the display [default 0]; option -lsp.
! URxvt*lineSpace: number

! True: handle Meta (Alt) + keypress to set the 8th bit. False: handle Meta (Alt) + keypress as an escape prefix [default].
! URxvt*meta8: boolean

! True: the mouse wheel scrolls a page full. False: the mouse wheel scrolls five lines [default].
! URxvt*mouseWheelScrollPage: boolean

! True: store tabs as wide characters. False: interpret tabs as cursor movement only; option "-ptab".
! URxvt*pastableTabs: boolean

! True: blink the cursor. False: do not blink the cursor [default]; option -bc.
! URxvt*cursorBlink: boolean

! True: Make the cursor underlined. False: Make the cursor a box [default]; option -uc.
! URxvt*cursorUnderline: boolean

! True: blank the pointer when a key is pressed or after a set number of seconds of inactivity. False: the pointer is
! URxvt*pointerBlank: boolean

! Mouse pointer foreground colour.
! URxvt*pointerColor: colour

! Mouse pointer background colour.
! URxvt*pointerColor2: colour

! Specifies number of seconds before blanking the pointer [default 2]. Use a large number (e.g. 987654321) to effectively
! URxvt*pointerBlankDelay: number

! The string to send when the backspace key is pressed. If set to DEC or unset it will send Delete (code 127) or, with
! URxvt*backspacekey: string

! The string to send when the delete key (not the keypad delete key) is pressed. If unset it will send the sequence
! URxvt*deletekey: string

! The characters used as delimiters for double-click word selection (whitespace delimiting is added automatically if
! URxvt*cutchars: string

!
! URxvt*{|}

! OverTheSpot, OffTheSpot, Root; option -pt.
! URxvt*preeditType: style

! name of inputMethod to use; option -im.
! URxvt*inputMethod: name

! The locale to use for opening the IM. You can use an "LC_CTYPE" of e.g.  "de_DE.UTF-8" for normal text processing but
! URxvt*imLocale: name

! Specify the font-set used for XIM styles "OverTheSpot" or "OffTheSpot". It must be a standard X font set (XLFD patterns
! URxvt*imFont: fontset

! Change the meaning of triple-click selection with the left mouse button. Instead of selecting a full line it will extend
! URxvt*tripleclickwords: boolean

! Enables "insecure" mode. Rxvt-unicode offers some escape sequences that echo arbitrary strings like the icon name or the
! URxvt*insecure: boolean

! Set the key to be interpreted as the Meta key to: alt, meta, hyper, super, mod1, mod2, mod3, mod4, mod5; option -mod.
! URxvt*modifier: modifier

! Specify the reply rxvt-unicode sends to the shell when an ENQ (control-E) character is passed through. It may contain
! URxvt*answerbackString: string

! Turn on/off secondary screen (default enabled).
! URxvt*secondaryScreen: boolean

! Turn on/off secondary screen scroll (default enabled). If this option is enabled, scrolls on the secondary screen will
! URxvt*secondaryScroll: boolean

! Turn on/off hold window after exit support. If enabled, urxvt will not immediately destroy its window when the program
! URxvt*hold: boolean

! Sets the working directory for the shell (or the command specified via -e). The path must be an absolute path and it must
! URxvt*chdir: path

! Compile frills: Associate action with keysym sym. The intervening resource name keysym. cannot be omitted.
! URxvt*keysym.sym: action

! URxvt*perl-ext-common: string

! Comma-separated list(s) of perl extension scripts (default: "default") to use in this terminal instance; option -pe.
! URxvt*perl-ext: string

! Perl code to be evaluated when all extensions have been registered. See the urxvtperl(3) manpage.
! URxvt*perl-eval: string

! Colon-separated list of additional directories that hold extension scripts. When looking for perl extensions, urxvt will
! URxvt*perl-lib: path

! Additional selection patterns, see the urxvtperl(3) manpage for details.
! URxvt*selection.pattern-idx: perl-regex

! Selection auto-transform patterns, see the urxvtperl(3) manpage for details.
! URxvt*selection-autotransform.idx: perl-transform

! This resource is deprecated and will be removed. Use a keysym resource instead, e.g.:
! URxvt*searchable-scrollback: keysym *DEPRECATED*

! Specifies the program to be started with a URL argument. Used by the "selection-popup" and "matcher" perl extensions.
! URxvt*url-launcher: string

! Compile frills: Sets the WM_TRANSIENT_FOR property to the given window id.
! URxvt*transient-for: windowid

! Compile frills: Sets override-redirect for the terminal window, making it almost invisible to window managers; option
! URxvt*override-redirect: boolean

! Turn on/off ISO 14755 (default enabled).
! URxvt*iso14755: boolean

! Turn on/off ISO 14755 5.2 mode (default enabled).
! URxvt*iso14755_52: boolean
```
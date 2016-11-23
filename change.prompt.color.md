#### 修改 `~/.bashrc`

Make sure all non-printable bytes in your PS1 are contained within `\[ \]`. Otherwise, bash will count them in the length of the prompt. It uses the length of the prompt to determine when to wrap the line.
See http://mywiki.wooledge.org/BashFAQ/053

也就是说,在bash中,所有在PS1中的非打印字符都必须用`"\[\]"`(不包括引号)将其包围起来,否则在计算提示符长度时也会将其计算在内,导致其无法正确地换行,也就出现了回到行首的情况.

#### my setting for PS1
`PS1='\[\e[33;1m\]\u@\h: \[\e[31m\]\W\[\e[0m\]$ '`

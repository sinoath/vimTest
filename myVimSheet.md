## Custom VIM Sheet

Topics:
- [Paging, how to move inside a text](#paging-how-to-move-inside-a-text)
- [Copy/paste (yank/put)](#copy-paste-(yank/put\))
- [Words and i (inner)]
- [search,highlighting]
- [replace]
- [Info line, Sort, Join, View, Read]
- [Jump list, change list]
- [Marks]
- [Find in line]
- [Visual mode]
- [.vimrc file]
- [Tab]
- [Buffers]
- [Split windows]
- [Tabs windows]
- [Folding text]

#### Paging, how to move inside a text

`ctrl-f` and `ctrl-b` - move Forward/Back 1 page at a time<br>
`ctrl-u` and `ctrl-d` - move Up/Down half a page at a time<br>
`gg` and `G` - move to the top or the bottom of the text<br>
`M` or `H` or `L` - move to the Middle, top (High) or bottom (Low) of the page<br>
`zz`, `zt`, `zb` - move the current line to the middle (z), to the top (t) or to the bottom (b)<br>
`ctrl-e` or `ctrl-y` - scroll the page down or up one line leaving the cursor in place (if the current cursor<br>
  line remain visible, otherwise the cursor will follow the scrolling)<br>
  a number [n] before this command set how many line scroll up or down<br>
[back to index](#custom-vim-sheet)

#### Copy/paste (yank/put)

`[n]Y` - yanks the entire line [n] number of time<br>
`[n]D` - delete [n] number of line, starting at the cursor position<br>
`[n]yy` or `[n]dd`	- yank or put [n] lines (copy/paste)<br>
`:set relativenumber` - show the line relative numbering
`:set number` - show the absolute line numbering (both can be used at the same time)<br>
[back to index](#custom-vim-sheet)


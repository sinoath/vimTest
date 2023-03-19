# Custom VIM Sheet

Topics:
- [Paging, how to move inside a text](#paging-how-to-move-inside-a-text)
- [Copy/paste (yank/put)]
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










### Paging, how to move inside a text

`^f` and `^b` - move Forward/Back 1 page at a time
`^u` and `^d` - move Up/Down half a page at a time
`gg` and `G` - move to the top or the bottom of the text
`M` or `H` or `L` - move to the Middle, top (High) or bottom (Low) of the page
zz, zt, zb - move the current line to the middle (z), to the top (t) or to the bottom (b)
ctrl-e or ctrl-y - scroll the page down or up one line leaving the cursor in place (if the current cursor
	line remain visible, otherwise the cursor will follow the scrolling)
	a number [n] before this command set how many line scroll up or down

## Custom VIM Sheet

Topics:
- [Paging, how to move inside a text](#paging-how-to-move-inside-a-text)
- [Copy/paste (yank/put)](#copypaste-yankput)
- [Words and i for inner](#words-and-i-for-inner)
- [search and highlighting](#search-and-highlighting)
- [replace](#replace)
- [Info line, Sort, Join, View, Read](#Info-line,-Sort,-Join,-View,-Read)
- [Jump list, change list](#Jump-list,-change-list)
- [Marks](#Marks)
- [Find in line](#Find-in-line)
- [Visual mode](#Visual-mode)
- [.vimrc file](#.vimrc-file)
- [Tab](#Tab)
- [Buffers](#Buffers)
- [Split windows](#Split-windows)
- [Tabs windows](#Tabs-windows)
- [Folding text](#Folding-text)

### Paging, how to move inside a text

`ctrl-f` and `ctrl-b` - move Forward/Back 1 page at a time<br>
`ctrl-u` and `ctrl-d` - move Up/Down half a page at a time<br>
`gg` and `G` - move to the top or the bottom of the text<br>
`M` or `H` or `L` - move to the Middle, top (High) or bottom (Low) of the page<br>
`zz`, `zt`, `zb` - move the current line to the middle (z), to the top (t) or to the bottom (b)<br>
`ctrl-e` or `ctrl-y` - scroll the page down or up one line leaving the cursor in place<br>
(if the current cursor line remain visible, otherwise the cursor will follow the scrolling)<br>
a number [n] before this command set how many line scroll up or down<br>
[back to index](#custom-vim-sheet)

### Copy/paste (yank/put)

`[n]Y` - yanks the entire line [n] number of time<br>
`[n]D` - delete [n] number of line, starting at the cursor position<br>
`[n]yy` or `[n]dd`	- yank or put [n] lines (copy/paste)<br>
`:set relativenumber` - show the line relative numbering
`:set number` - show the absolute line numbering (both can be used at the same time)<br>
[back to index](#custom-vim-sheet)

### Words and i (for inner)

`[n]w` move to the start of the next word, <br>
`[n]W` same, but ignoring special characters like.the.dot [n] times<br>
`[n]e` move to the end of the next word, E ignore the special characters<br>
`[n]ge` same but backwards, gE ignore special characters<br>
`D` or `C` - delete or change from the cursor position to the end of the line<br>
`i` - select inside a text object (word, parenthesis, quotes and so on)<br>
[back to index](#custom-vim-sheet)

### search and highlighting

`/`	- start the search of a characters pattern<br>
`*`	- search forward every occurency of the word under cursor<br>
`#`	- same, but backward<br>
`:nohl`	- set temporary off the highlight<br>
`:set [no]hlsearch`	- set highlight on/off<br>
`:set [no]incsearch` -  this enable the incremental highlight on search (on/off)<br>
`/\c`	- search case insensitive pattern of characters<br>
`\`	- used as an escape character to search for a special one (like `/\*` search for an asterisk) <br>
[back to index](#custom-vim-sheet)

### replace
`:[n],[m]s/this/that` - search from line 'n' to line 'm' the word 'this' and substitute with 'that'<br>
`:%s/this/that` - same, but search the entire document<br>
`/g` - means globally, every occurrency, at the end of a search and replace command<br>
adding `i` is case insensitive, adding `I` is case sensitive
adding `c` it will ask for a confirm
`\<word\>` - both in search and replace, it will find 'word' as a single word,
case insensitive and skipping **password** (i.e. `%s/\<word\>/warlords/gi` will substitute 
**word** as a single word with **warlords** for the entire document, for every occurrency
[back to index](#custom-vim-sheet)

### Info line, Sort, Join, View, Read

`ctrl-g` - show the infoline, with the filename, number of lines and the position of the cursor<br>
as a percentage of the file<br>
`:[n][m]sort` - ascending sort from line **n** to line **m** or use `%` to sort the whole file<br>
`sort!` - same, but in descending order<br>
`J` - Capital **J** join the current line to the line below, a number can precede the command<br>
to join more than 1 line at a time<br>
`:view` - Open a file in read only mode<br>
`:read` - read the content of a file and insert it on cursor position<br>
[back to index](#custom-vim-sheet)

### Jump list, change list:

`g,` - Go forwart to the next (more recent) edit point of the text<br>
`g;` - same, going backwards<br>
`gi` - place the cursor at the last insert position and enter INSERT mode<br>
`^o` - move to the previous jump<br>
`^i` - move to the next jump<br>
`:changes` - open the whole list of changes made inside the text<br>
`:jumps` - open the jumps list. Vim considers jumps: the use of marks, search or replaces, open a different file.<br>
Paging or scrolling through the page (like using hjkl) are NOT considered jumps<br>
[back to index](#custom-vim-sheet)

### Marks:

`m[letter]` - set a (book)mark, lowercase for just the file, uppercase globally.<br>
meaning that every file can have an 'a' mark, just one file can have 'A' mark<br>
`'a` or` ``a` - move to the line or the line and character when **a** mark was set<br>
Any lower case letter can be used as a mark.<br>
Changing file if using **uppercase letter**, if it was set on a different file<br>
(set a mark on the 's' of 'Marks' word to try<br>
`['` and `]'` - navigate marks lines, backward/forward<br>
`[`` `and `]`` `- same but for lines and character position<br>
`:marks` - show the list of (book)marks<br>
`:delmarks` - appending `!` delete all marks, adding `c-f` delete a range of marks (c through f), <br>
`a f T` delete a specific list of marks (marks a, f and T in this case)<br>
[back to index](#custom-vim-sheet)

### Find in line:

`f[character]` or `F[character]` - find the next or previous [character] in current line<br>
`t[character]` or `T[character]` - same but it stops one character the [character], so it search Till **[character]**<br>
both of them can be combined with yank and delete commands<br>
`d/[pattern]` - delete in line all character forward up until **[pattern]** , NOT including [pattern]<br>
`d?[pattern]` - same but backward, it will erase all characters INCLUDING [pattern]<br>
[back to index](#custom-vim-sheet)

### Visual mode:

`v` - enter visual mode; V - enter in **visual line** mode<br>
`ctrl-v` - enter in the **visual block** mode<br>
now I can select the text using the same commands to move the cursor (hjkl, w, e and so on)<br>
or the find in line commands. i can be used as 'in', like 'i(' select all text inside the parenthesis<br>
`y` and `p` - yank and paste the selected text. IPORTANT: when pasting something, the 'visual mode buffer'<br>
will be overwritten but the new selected text, useful for switch a pattern, not for pasting more than once<br>
[back to index](#custom-vim-sheet)

### .vimrc file

`nmap` - map a key to execute a command in normal mode<br>
`imap` - same, but in insert mode<br>
`let mapleader = '[key]'` - set a key as **leader** so that pressing that key and a shortcut execute a command<br>
(as an example setting `,` as leader, some action can be assigned to `,i` avoiding to enter in INSERT mode)<br>
`abbr [pattern-a][pattern-b]` - writing `pattern-a` and a space, it will write `pattern-b`<br>
[back to index](#custom-vim-sheet)

### Tab

`<<` or `>>` - outdent or indent a line. Can be combined with [n]j or [n]k to indent/outdent current line and the [n]<br>
lines below/above. Visual select could also be used to select lines and outdent/indent. All apply in NORMAL mode<br>
In INSERT mode TAB key is used to indent/outdent (TIP - `:set list` show invisible characters like tab or CR)<br>
in this mode pressing `ctrl-v` and typing u0009, will insert a 'TAB character' (visible as `^I` when using `:set list`)<br>
Alternatively pressing `ctrl-v` and `ctrl-i` do the same thing<br>
Invisible characters can be customized, unicode symbol for TAB is u2192 and unicode symbol for eol is u21b2<br>
in .vimrc file using `set listchars=tab:` and typing `ctrl-v` followed by the unicode u2192 we can set TAB invisible<br>
character. appending to the same line `\ ,eol:` and typing `ctrl-v` and than `u21b2` I can change eol character too<br>
`:set expandtab` - Convert a TAB in a number of spaces characters, apply to << and >> too<br>
`:set noexpandtab` - revert to the TAB character<br>
`:set sw` or `:set swiftwidth` - show how many spaces the TAB character will be converted to, appen '=[n]' to set this number to n<br>
`:set ts` or `:set tabstop` - show how many 'spaces wide' are TAB characters, append `=[n]` to set as "n spaces wide"<br>
`:set sts` of `:set softtabstop` - set the TAB stop in INSERT mode, if set to 0 it will follow the tabstop setting.<br>
As the previous commands, append `=[n]` to set as 'n number of spaces wide'<br>
- Behaviour: if `set tabstop=4` `set softtabstop=0` `set expandtab` are used<br>
in INSERT mode a TAB will insert 4 spaces, and will treat as 4 characters, hence got to press BACKSPACE 4 times to delete<br>
- Behaviour: if `set tabstop=4` `set softtabstop=4` `set expandtab` are used<br>
in INSERT mode TAB write spaces like before, but BACKSPACE cancel all the spaces at once BUT ONLY IF no more spaces are added<br>
this way BACKSPACE needs to be used 5 times (with the settings above) to delete the TAB<br>
`:set ts sts sw` - show all three settings at once; in general they are set to the same number of spaces<br>
`filetype indent on` - in .vimrc set custom indentation based on different file types.<br>
`autocmd Filetype cpp setlocal noexpandtab ts=4 sts=4 sw=4` - in .vimrc set custom values everytime a cpp file is loaded in vim<br>
[back to index](#custom-vim-sheet)

### Buffers

`:buffers` or `:ls` - show the list of buffers. `#` mean the previous one, `%a` means active buffer
a `+` means there are unsaved changes in that buffer
`:edit` or `:e filename` - open in edit mode filename, putting the previous file in a buffer
`:e!` - put the file in the last saved state, in other words in the state the file was last time wass issued :w
`:bp` or `bn` - go to the previous/next buffer (inside the buffers list)
`:set hidden` - avoid to show warning message when switching buffer without saving changes in the current one
this apply to all files in the buffer, not just the current one
`:bd` - delete a buffer. If a change was made on that file, it'll show a warning message, 
even if `:set hidden` was set

### Split windows

`:sp` or `:vsp` - split window horizontally or vertically, even for the same file. So I can work on different places
of the text/code inside the file
appending 'filename', it will split open filename instead of a copy of the file itself
`:set splitright` - invert the default behavior, showing the vertical split window to the right instead of left
`:resize` - accept numbers for an absolute resizing, or +/-[n] for relative resizing
`:vertical resize` - same but vertically
`:ba` or :ball - shows all buffers in split windows
`:vert ba` - same but vertically
`:[vert] 3ba` -  shows the first 3 buffers
`:vsp | b2` - open the buffer 2 in a vertical split window (mandatory use of '|' character, otherwise it'll open
buffer 2 as a new window)
`:ba` or `:ball `- shows all buffers in split windows
`:vert ba` - same but vertically
`:[vert] 3ba` -  shows the first 3 buffers
`:vsp | b2` - open the buffer 2 in a vertical split window (mandatory use of '|' character, otherwise it'll open
buffer 2 as a new window)
`ctrl-w` - escape command for windows. (remapped to Alt-a, tmux style) After that:
- `w` switch window cycling through them
- `hjkl` move to the window vim-style, so 'h' left, 'j'down and so on
- `x` swap windows
- `r` or 'R' rotate the split windows in one direction or the opposite
- `t` or 'b' move to the (t)op left window or the (b)ottom right window
- `p` move to the previous window
- `s` split window
- `=` make the windows eaqually sized
- `-` or '|' maximizes height/width of the current window
- `o` shows (o)nly the current window, putting into buffers the other ones
`:help ctrl-w` - open a comprehensive help page for split windows commands
[back to index](#custom-vim-sheet)

### Tabs windows

`:tabedit` or `tabe [filename]` - open a new tab same way as split commands, with the file itself or "filename"<br>
`:tabn [n]` or `:tabp [n]` - got to the [n] next/previous tab<br>
`[n]gt` or `[n]gT` do the same<br>
`:tabnew` - open an empty new tab. The time is unnamed untile a file is saved.<br>
The tab have the same name of the split window I'm in<br>
`:tabm [n]` - move the tab to the [n] position, 0 meaning the far left. If no [n] are typed, move the tab to the far right<br>
`:tabclose` or `:q` - close a single tab and put it in a buffer<br>
`:tabclose n` - closes the n tab, far left is 1<br>
`:tab ball` - opens all the buffers in separate tabs, limited to tabepagemax value<br>
`:tab sb [n]` - open a new tab with the [n] buffer in it (see Buffer section sb or splitbuffer)<br>
`:set tabpagemax [n]` - set the max number of tabs, or shows the setting if no [n] is typed<br>
`:tabonly` - close all tabs but the one I'm currently in<br>
`:drop [filename]` - substitute with a 'filename' tab the current one. If the file is already open in a tab, will move to that tab<br>
- split windows can be used inside a tab, see [Split](#split-windows) section<br>
`:tab split` - open the current split window in a new tab, leaving the split in place<br>
`ctrl-w T` - same as tab split, but closes the split window too<br>
`:qa` - closes all tabs<br>
[back to index](#custom-vim-sheet)

### Folding text

**TIP:** Easier to practice with a code file (python, css, cpp or else)<br>
folds are lost on file close, unless a mkview file is created (and loaded after the file is open)<br>
can add a section in .vimrc to auto make a view and silently auto load a view (see .vimrc file)<br>
`:mkview` - create a make view file (mkview)<br>
`:loadview` - load a previously saved view<br>
`:set foldmethod` or `:set fdm` - show (or set) the fold method in use. The default one is 'manual'<br>
`:[n],[m]fold` or `[n],[m]fo` - create a fold from line 'n' to line 'm'<br>
`:,+[n]fo` - create a fold for the current line and the next 'n' lines<br>
`:,-[n]fo` - same but the previous [n] lines<br>
`zf` - after a visual selection, it will create a fold. ('z' remind of a folding paper, many commands use it)<br>
`zo` and `zc` - open/close a fold<br>
`zf[motion]` - create a folder based on that motion exemples are:<br>
- `zf2j` create a fold for current line and 2 lines under<br>
- `zfip` create a fold for the paragraph the cursor is in<br>
- `zfa{` create a fold for a code block inside curly braces<br>
- `va{` and `zf` has the same effect, first command visual select text inside curly braces, and `zf` create the fold<br>
`zn` - open all folders, but if a folder was manually closed it stay closed<br>
`zN` - close all folders, but if a folder was manually opened it stays opened<br>
`:[n][m] foldopen` - open folds from line 'n' to line 'm'.<br>
`:[n][m] foldclose` - close folds from line 'n' to line 'm'.<br>
`:% foldopen` - select the entire document and open all folds. Same apply to foldclose<br>
`zj` and `zk` - move to the next/previous folder. IMPORTANT: zk move the cursor to the last line of the previous folder!<br>
`[z` and `]z` - move to cursor to the top/bottom line of the current folder<br>
`zd` - delete the current folder<br>
`zE` - delete all the folders in the document<br>
Folds can be nested:<br>
`zO` and `zC` - open/close the current fold and all inner/outer nested ones<br>
`zA` - toggles between zC and zO<br>
`zr` and `zm` - close/open all folds by one level<br>
`zR` and `zR` - act like `zC` and `zO` but for all folds<br>

	another for test



	this file has no indentation (yet) file
	this file has no indentation (yet)

just writing other words in here
for the purpose of learning this editor



trying branch features

playlist I'm watching:
https://www.youtube.com/watch?v=1lzXr-MztOU&list=PLy7Kah3WzqrEjsuvhT46fr28Q11oa5ZoI
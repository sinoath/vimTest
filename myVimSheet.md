## Custom VIM Sheet

| Topics: |  |
| :-- | :-- |
|  [Paging, how to move inside a text](#paging-how-to-move-inside-a-text) | [Tab](#tab)
|  [Copy/paste (yank/put)](#copypaste-yankput) | [Buffers](#buffers)
|  [Words and i for inner](#words-and-i-for-inner) | [Split windows](#split-windows)
|  [Search and Highlighting](#search-and-highlighting) | [Window tabs](#window-tabs)
|  [replace](#replace) | [Folding text](#folding-text)
|  [Info line, Sort, Join, View, Read](#info-line-sort-join-view-read) | [netrw](#netrw)
|  [Jump list, change list](#jump-list-change-list) | [vimgrep](#vimgrep)
|  [Marks](#marks) | [Registers](#registers) | [Registers](#registers)
|  [Find in line](#find-in-line) | [Bonus topic: Plugins](#bonus-topic-plugins)
|  [Visual mode](#visual-mode)
|  [.vimrc file](#vimrc-file)


### Paging, how to move inside a text

`h` and `l` - move left/right the cursor by one character<br>
`j` and `k` - move down/up the cursor by one line<br>
`0` and `$` - move the cursor to the first/last character in a line<br>
`^` and `g_` - move the cursor to the first/last non blank character in the line<br>
`ctrl-f` and `ctrl-b` - move Forward/Back 1 page at a time<br>
`ctrl-u` and `ctrl-d` - move Up/Down half a page at a time<br>
`ctrl-e` or `ctrl-y` - scroll the page down or up one line leaving the cursor in place<br>
if the current cursor line remain visible, otherwise the cursor will follow the scrolling.<br>
A number [count] before the commands above set how many times execute this movement<br>
`gg` and `G` - move to the top or the bottom of the text<br>
A number [count] before the commands above set the absolute line number the cursor move to<br>
`M` or `H` or `L` - move the cursor to the Middle, top (High) or bottom (Low) of the page<br>
`zz`, `zt`, `zb` - move the current line to the middle (z), to the top (t) or to the bottom (b)<br>
[back to index](#custom-vim-sheet)

### Copy/paste (yank/put)

`[count]Y` - yanks the entire line [count] number of time<br>
`[count]D` - delete [count] number of line, starting at the cursor position<br>
`[count]yy` or `[count]dd`	- yank or put [count] lines (copy/paste)<br>
`y` and `d` can be used in combination of any kind of 'cursor movement' or text object<br>
`:set relativenumber` - show the line relative numbering<br>
`:set number` - show the absolute line numbering (both can be used at the same time)<br>
`p` - paste after the character or under the line the cursor is in
`P` - same, but before the caracter or the line above the cursor
[back to index](#custom-vim-sheet)

### Words and i (for inner)

`[count]w` move to the start of the next word,<br>
`[count]W` same, but ignoring special characters like the dot or underscore [count] times<br>
`[count]e` move to the end of the next word, `E` ignore the special characters<br>
`[count]ge` same but backwards, `gE` ignore special characters<br>
`D` or `C` - delete or change from the cursor position to the end of the line<br>
`i` - select inside a text object (word, parenthesis, quotes and so on)<br>
[back to index](#custom-vim-sheet)

### Search and Highlighting

`/`	- start the search forward of a characters pattern<br>
`?`	- start the search backward of a characters pattern<br>
`*`	- search forward every occurency of the word under cursor<br>
`#`	- same, but backward<br>
`:set [no]hlsearch`	- set highlight on/off<br>
`:set [no]incsearch` -  this enable the incremental highlight on search (on/off)<br>
Once search is used, highlight stays on until it is manually turned off<br>
`:nohl`	- set temporary off the highlight<br>
`/\c` - search case insensitive pattern of characters<br>
`\`	- used as an escape character to search for a special one (like `/\*` search for an asterisk)<br>
[back to index](#custom-vim-sheet)

### Replace
`:[n],[m]s/this/that` - search from line 'n' to line 'm' the word 'this' and substitute with 'that'<br>
`:%s/this/that` - same, but search the entire document<br>
`/g` - means globally, every occurrency, at the end of a search and replace command<br>
adding `i` is case insensitive, adding `I` is case sensitive<br>
adding `c` it will ask for a confirm<br>
`\<word\>` - both in search and replace, it will find 'word' as a single word,<br>
case insensitive and skipping **password** (i.e. `%s/\<word\>/warlords/gi` will substitute<br>
**word** as a single word with **warlords** for the entire document, for every occurrency<br>
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

### Jump list, Change list:

`g,` - Go forwart to the next edit (change) point of the text<br>
`g;` - same, going backwards<br>
`^o` - move to the previous jump<br>
`^i` - move to the next jump<br>
a [count] number before these commands executes them [count] number of time<br>
`gi` - place the cursor at the last insert position and enter INSERT mode<br>
`:changes` - open the whole list of changes made inside the text<br>
`:jumps` - open the jumps list. Vim considers jumps: the use of marks, search or replaces, open a different file.<br>
Paging or scrolling through the page (like using hjkl) are NOT considered jumps<br>
[back to index](#custom-vim-sheet)

### Marks:

`m[letter]` - set a (book)mark, lowercase for just the file, uppercase globally. With upper case mark,<br>
it will jump to the file that have that mark set. Every file can have 'a' mark, just one file can have 'A' mark<br>
`'a` or` ``a` - move to the line or the line and character when **a** mark was set<br>
`['` and `]'` - navigate marks lines, backward/forward<br>
`[`` `and `]`` `- same but for lines and character position<br>
`:marks` - show the list of (book)marks<br>
`:delmarks` - appending `!` delete all marks, adding ` c-f` delete a range of marks (c through f),<br>
` a f T` delete a specific list of marks (marks a, f and T in this case)<br>
[back to index](#custom-vim-sheet)

### Find in line:

`f[character]` or `F[character]` - find the next or previous [character] in current line<br>
`t[character]` or `T[character]` - same but it stops one character, so it search Till **[character]**<br>
both of them can be combined with yank and delete commands<br>
`d/[pattern]` - delete in line all character forward up until **[pattern]** , NOT including [pattern]<br>
`d?[pattern]` - same but backward, it will erase all characters INCLUDING [pattern]<br>
[back to index](#custom-vim-sheet)

### Visual mode:

`v` - enter visual mode; `V` - enter in **visual line** mode<br>
`ctrl-v` - enter in the **visual block** mode<br>
This modes can select the text using the same commands to move the cursor (hjkl, w, e and so on)<br>
or the find in line commands. `i` can be used as `in`, like `i(` select all text inside the parenthesis<br>
`y` and `p` - yank and paste the selected text. IPORTANT: when pasting something, the 'visual mode buffer'<br>
will be overwritten but the new selected text, useful for switch a pattern, not for pasting more than once<br>
`c` - delete the selected text and change to INSERT mode
[back to index](#custom-vim-sheet)

### .vimrc file

`nmap` - map a key to execute a command in normal mode<br>
`imap` - same, but in insert mode<br>
`nnoremap` - set a **no recursive** mapping, meaning it can call itself, in NORMAL mode
`inoremap` - same but for INSERT mode
`let mapleader = '[key]'` - set a key as **leader** so that pressing that key and a shortcut execute a command<br>
(as an example setting `,` as leader, some action can be assigned to `,i` avoiding to enter in INSERT mode)<br>
`abbr [pattern-a][pattern-b]` - writing `pattern-a` and a space, it will write `pattern-b`<br>
Fix fuzzy search:<br>
`set nocompatible` - Limit search to your project<br>
`set path+=\*\*` - Search all subdirectories and recursively<br>
`set wildmenu` - Shows multiple matches on one line<br>
[back to index](#custom-vim-sheet)

### Tab

`<<` or `>>` - outdent or indent a line.<br>
`<` or `>`hcan be combined with [count]j or [count]k to indent/outdent current line and the [count]<br>
lines below/above. Visual select could also be used to select lines and outdent/indent. All apply in NORMAL mode<br>
In INSERT mode TAB key is used to indent/outdent (TIP - `:set list` show invisible characters like tab or CR)<br>
in this mode pressing `ctrl-v` and typing u0009, will insert a 'TAB character'<br>
(visible as `^I` when using `:set list`)<br>
Alternatively pressing `ctrl-v` and `ctrl-i` do the same thing<br>
Invisible characters can be customized, unicode symbol for TAB is u2192 and unicode symbol for eol is u21b2<br>
in .vimrc file using `set listchars=tab:` and typing `ctrl-v` followed by the unicode u2192 we can set TAB invisible<br>
character. appending to the same line `\ ,eol:` and typing `ctrl-v` and than `u21b2` I can change eol character too<br>
`:set expandtab` - Convert a TAB in a number of spaces characters, apply to `<<` and `>>` too<br>
`:set noexpandtab` - revert to the TAB character<br>
`:set sw` or `:set swiftwidth` - show how many spaces the TAB character will be converted to, appen `=[count]` to set this number to count<br>
`:set ts` or `:set tabstop` - show how many 'spaces wide' are TAB characters, append `=[count]` to set as "count spaces wide"<br>
`:set sts` of `:set softtabstop` - set the TAB stop in INSERT mode, if set to 0 it will follow the tabstop setting.<br>
As the previous commands, append `=[count]` to set as 'count number of spaces wide'<br>
- Behaviour: if `set tabstop=4` `set softtabstop=0` `set expandtab` are used<br>
in INSERT mode a TAB will insert 4 spaces, and will treat as 4 characters, hence got to press BACKSPACE 4 times to delete<br>
- Behaviour: if `set tabstop=4` `set softtabstop=4` `set expandtab` are used<br>
in INSERT mode TAB write spaces like before, but BACKSPACE cancel all the spaces at once UNLESS more spaces are added<br>
Adding a space, BACKSPACE needs to be used 5 times (with the settings above) to delete the TAB<br>
`:set ts sts sw` - show all three settings at once; in general they are set to the same number of spaces<br>
`filetype indent on` - in .vimrc set custom indentation based on different file types.<br>
`autocmd Filetype cpp setlocal noexpandtab ts=4 sts=4 sw=4` - in .vimrc set custom values everytime a cpp file is loaded in vim<br>

[back to index](#custom-vim-sheet)

### Buffers

`:buffers` or `:ls` - show the list of buffers. `#` mean the previous one, `%a` means active buffer<br>
a `+` means there are unsaved changes in that buffer, `h` means hidden<br>
`:edit` or `:e filename` - open in edit mode filename, putting the previous file in a buffer<br>
`:e!` - put the file in the last saved state, in other words revert all changes to the last `:w` issued<br>
`:bp` or `bn` - go to the previous/next buffer (inside the buffers list)<br>
`:set hidden` - avoid to show warning message when switching buffer without saving changes in the current one<br>
this apply to all files in the buffer, not just the current one<br>
`:bd` - delete a buffer.<br>
If a change was made on that file, it'll show a warning message,<br> even if `:set hidden` was set<br>
[back to index](#custom-vim-sheet)

### Split windows

`:sp` or `:vsp` - split window horizontally or vertically, for the same file. So I can work on different places<br>
of the text/code inside the file<br>
appending ` filename`, it will split open filename instead of a copy of the file itself<br>
`:set splitright` - invert the default behavior, showing the vertical split window to the right instead of left<br>
`:resize` - accept numbers for an absolute resizing, or +/-[count] for relative resizing<br>
`:vertical resize` - same but vertically<br>
`:ba` or `:ball` - shows all buffers in split windows<br>
`:vert ba` - same but vertically<br>
`:[vert] 3ba` -  shows the first 3 buffers horizontally [vertically]<br>
`:vsp | b2` - open the buffer 2 in a vertical split window (mandatory use of '|' character,<br>
otherwise it'll open buffer 2 as a new window)<br>
`ctrl-w` - escape command for windows. Commands after the escape are:<br>
- `w` switch window cycling through them<br>
- `hjkl` move to the window vim-style, so 'h' left, 'j'down and so on<br>
- `x` swap windows<br>
- `r` or `R` rotate the split windows in one direction or the opposite<br>
- `t` or `b` move to the (t)op left window or the (b)ottom right window<br>
- `p` move to the previous window<br>
- `s` split window<br>
- `=` make the windows eaqually sized<br>
- `-` or `|` maximizes height/width of the current window<br>
- `o` shows (o)nly the current window, putting into buffers the other ones<br>
- `T` close the split window and open it in a new Tab. See [Window tabs](#window-tabs)

`:help ctrl-w` - open a comprehensive help page for split windows commands<br>
[back to index](#custom-vim-sheet)<br>

### Window tabs

`:tabedit` or `tabe [filename]` - open a new tab same way as split commands, with the file itself or `filename`<br>
`:tabn [count]` or `:tabp [count]` - got to the [count] next/previous tab<br>
`[count]gt` or `[count]gT` do the same in NORMAL mode<br>
`:tabnew` - open an empty new tab. The time is unnamed untile a file is saved.<br>
The tab have the same name of the split window I'm in<br>
`:tabm [count]` - move the tab to the [count] position, 0 meaning the far left. If no [count] are typed, move the tab to the far right<br>
`:tabclose` or `:q` - close a single tab and put it in a buffer<br>
`:tabclose [count]` - closes the [count] tab, far left is 1<br>
`:tab ball` - opens all the buffers in separate tabs, limited to tabepagemax value<br>
`:tab sb [count]` - open a new tab with the `[count]` buffer in it (see Buffer section sb or splitbuffer)<br>
`:set tabpagemax [count]` - set the max number of tabs, or shows the setting if no `[count]` is typed<br>
`:tabonly` - close all tabs but the one I'm currently in<br>
`:drop [filename]` - substitute with a `filename` tab the current one. If the file is already open in a tab, will move to that tab<br>
- split windows can be used inside a tab, see [Split](#split-windows) section<br>
`:tab split` - open the current split window in a new tab, leaving the split in place<br>
`ctrl-w T` - same as tab split, but closes the split window too<br>
`:qa` - closes all tabs<br>

[back to index](#custom-vim-sheet)

### Folding text

**TIP:** Easier to practice with a code file (python, css, cpp or else)<br>
folds are lost on file close, unless a mkview file is created (and loaded after the file is open)<br>
can add a section in .vimrc to auto make a view and silently auto load a view (see [.vimrc file](#vimrc-file))<br>
`:mkview` - create a make view file (mkview)<br>
`:loadview` - load a previously saved view<br>
`:set foldmethod` or `:set fdm` - show (or set) the fold method in use. The default one is 'manual'<br>
`:[n],[m]fold` or `[n],[m]fo` - create a fold from line 'n' to line 'm'<br>
`:,+[n]fo` - create a fold for the current line and the next 'n' lines<br>
`:,-[n]fo` - same but the previous [n] lines<br>
`zf` - after a visual selection, it will create a fold. ('z' remind of a folding paper)<br>
`zo` and `zc` - open/close a fold<br>
`zf[motion]` - create a folder based on that motion, examples are:<br>
- `zf2j` create a fold for current line and 2 lines under<br>
- `zfip` create a fold for the paragraph the cursor is in<br>
- `zfa{` create a fold for a code block inside curly braces<br>
- `va{` and `zf` has the same effect, first command visual select text inside curly braces, and `zf` create the fold<br>

`zn` - open all folders, but if a folder was manually closed it stays closed<br>
`zN` - close all folders, but if a folder was manually opened it stays opened<br>
`:[count][m] foldopen` - open folds from line 'count' to line 'm'.<br>
`:[count][m] foldclose` - close folds from line 'count' to line 'm'.<br>
`:% foldopen` - select the entire document and open all folds. Same apply to foldclose<br>
`zj` and `zk` - move to the next/previous folder. IMPORTANT: `zk` move the cursor to **the last line** of the previous folder!<br>
`[z` and `]z` - move to cursor to the top/bottom line of the current folder<br>
cursor needs to be inside the fold to work<br>
`zd` - delete the current folder<br>
`zE` - delete all the folders in the document<br>
Folds can be nested:<br>
`zO` and `zC` - open/close the current fold and all inner/outer nested ones<br>
`zA` - toggles between zC and zO<br>
`zr` and `zm` - close/open all folds by one level<br>
`zR` and `zR` - act like `zC` and `zO` but for all folds<br>
[back to index](#custom-vim-sheet)


### netrw

`vim nameDir` - Open vim netrw plugin for the directory `nameDir`<br>
in netrw:<br>
- `gh` - show/hide the dot files<br>
- `I` - show/hide the top banner<br>
- `s` - change file sorting filter<br>

moving the cursor up with the vim motions (`hjkl`) the top part of netrw shows hints, commands,<br>
shortcuts, quick help and so on<br>
to change a setting in this section press `ENTER` (for example to change the sort filter)<br>
when navigating inside directories, we can select a file with `ENTER` to open it, but using `:q` will close<br>
vim completelly.<br>
with the cursor on a file we can split open it<br>
- `o` - horizontally<br>
- `v` - vertically<br>
- `p` - preview it<br>

preview is (by default) a horizontal split open window, but leave the cursor on netrw,<br>
while `o` and `v` split open the window **and** move the cursor to it<br>
`:let g:netrw_preview=1` - change the split preview from horizontal to vertical<br>
the vertical split will open to the left, unless specifing to open on the right side with the command `:let g:netrw_altv=1`<br>
`:Vex` or `:Sex` - when a file is opened in vim, these commands split open vertically or horizontally a netrw window<br>
These next three lines are for the fuzzy search in .vimrc:<br>
`set nocompatible` - Limit search to your project<br>
`set path+=\*\*` - Search all subdirectories and recursively<br>
`set wildmenu` - Shows multiple matches on one line<br>
[back to index](#custom-vim-sheet)




### vimgrep

`:vimgrep /regex/[option] target` - Search for the regular expression in the target file/directory,<br>
with the g option it will count the occurencies<br>
`:copen` of `:cope` or `:cw` - open the list of the regex occurencies<br>
`:cnext` and `:cprev` - move to the next/previous regex occurency<br>
`:cfirst` and `:clast` - move to the first/last occurency<br>
How to search in the entire project directory (it is set when vim opens):<br>
`:pwd` - show the actual directory<br>
`:vimgrep /regex/g **/*` - this target means to search in the entire project directory (fuzzy search fix NEEDED)<br>
[back to index](#custom-vim-sheet)




### Registers

Registers are memory locations vim uses to store yanked and deleted text, or macros<br>
`"[letter]` - is used to call [letter] register, in NORMAL and VISUAL mode<br>
Appending to a register call an action like yank, delete or change, the text will be stored in that register<br>
`ctrl-r` - call a register in INSERT mode and write it<br>
`:reg` - show registers list<br>
`"[uppercase-letter]` - will **append** the text to the conent of the **letter** register<br>
Special registers.<br>
- `""` - default register, overwritten everytime some register is changed (including standard use of yank, delete and so on)<br>
- `"/` - contains latest string used for a search forward<br>
- `"?` - contains latest string used for a search backward<br>
- `"*` - store the 'under the cursor' search<br>
- `"%` - name of the file<br>
- `":` - last command issued in command mode<br>
- `".` - register that contain the command to repeat with the `.` in vim<br>
- `"-` - register used to store deleted text<br>
- `"0` - register used as a 'backup' when yanking<br>
- `"1` to `"9` - registers used as a 'backup' when deleting lines, 1 being the most recent<br>
`:let @[letter]=""` - delete the content of a register, or store the text inside quotes.<br>
Another use for this command is to copy a register into another one: `let @count=@m`<br>
or assign a text string to a register<br>
TIP: to modify a register (say `m`), `:let @m="`, than `ctrl-r` to call the register in INSERT mode,<br>
`m` in this case. Edit the string and remember to close the `"`<br>
[back to index](#custom-vim-sheet)




### Bonus topic: Plugins

- Repeat.vim - from https://tpope.io/vim/repeat.git it makes the `.` repeat function able to repeat<br>
plugins too<br>
- tpope/vim-fugitive - add the `:G` or `Git` command, that act like `git` in bash<br>
- tpope/vim-surround - surround a text object with quotes, parentheses or even html tags<br>
	* `cs"'` - change the surrounding from `"` to `'`<br>
	* `cst"` - change the surrounding html tag to `"`<br>
	* `ys[movement]"` - add to the movement (or text object) the `"` surround<br>
	* `ds"` - delete the surrond `"` based on the cursor position<br>
	* `yss"` - surround with `"` the entire line<br>
	* `.` - works with `ds`, `cs` and `ys`<br>
- tpope/vim-commentary - adds/delete comments to text objects and movements based on the file extension<br>
`gc[movement]` - enable/disable comments for the movement (or the text object)<br>
- michaeljsmith/vim-indent-object - define a new object as an indented text, commands are:<br>
* `<count>ai` - An Indentation level and line above.<br>
* `<count>ii` - Inner Indentation level (no line above).<br>
* `<count>aI` - An Indentation level and lines above/below.<br>
* `<count>iI` - Inner Indentation level (no lines above/below).<br>



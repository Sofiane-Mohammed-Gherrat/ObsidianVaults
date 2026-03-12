---
from: youtube
created: 2025-08-22
tags:
  - inbox
  - IDE
source: https://www.youtube.com/watch?v=fw5U551BZWs
---
[![](https://yt3.ggpht.com/lxGSC6-yRXCG9V2Gn-ecKU-29bNL-ID7qhq7UsNfEiyz-NFbL3ucs60PcOTadYNGYUgoBuAx=s88-c-k-c0x00ffffff-no-rj)](https://www.youtube.com/@joseanmartinez)
[Josean Martinez](https://www.youtube.com/@joseanmartinez)

---

# 📌 Points Covered in the Video

1. **Opening & Exiting Vim/Neovim**
    
    - Opening files or projects (`vim`, `nvim filename`)
    - Normal mode is default
    - Save & quit commands
    
2. **Navigation Basics (motions & movement)**
    
    - HJKL as arrow keys
    - Horizontal, vertical, word, paragraph, line, and screen navigation
    
3. **Searching & Jumping**
    
    - Search with `/` or `?`
    - Find word under cursor
    - Jump list navigation
    
4. **Insert & Editing Modes**
    
    - Entering/exiting insert mode
    - Undo, redo
    
5. **Operators & Editing Text**
    
    - Yank (copy), delete, change, paste
    - Motions combined with operators
    - Line-wise operations
    
6. **Visual Mode**
    
    - Selecting visually and applying operators
    
7. **Search & Replace**
    
    - Substitutions with confirmation
    
8. **Text Objects**
    
    - Words, paragraphs, quotes, parentheses, braces, tags
    - Inner (`i`) vs. around (`a`)
    - Cycling visual selections
    
9. **Efficiency & Muscle Memory**
    
    - Encouragement to practice to become faster.
    

---

# 📖 Vim Shortcuts (Grouped)

### 1. **File & Mode Management**

- `:q` → Quit

- `:w` → Save

- `:wq` → Save and quit

- `Esc` → Back to normal mode
 

### 2. **Basic Movement (HJKL)**

- `h` → Left

- `l` → Right

- `j` → Down

- `k` → Up

- `5h`, `5j` … → Repeat movement n times


### 3. **Line Navigation**

- `0` → Start of line

- `^` → First non-blank char

- `$` → End of line


### 4. **Character Searching**

- `f<char>` → Find next char

- `F<char>` → Find previous char

- `t<char>` → Till before char

- `T<char>` → Till before char backwards

- `;` → Repeat forward

- `,` → Repeat backward


### 5. **Word Navigation**

- `w` → Start of next word

- `e` → End of word

- `b` → Start of previous word

- `W`, `E`, `B` → Same but include symbols


### 6. **Paragraphs & Blocks**

- `{` → Previous paragraph

- `}` → Next paragraph


### 7. **Line & File Navigation**

- `gg` → First line

- `G` → Last line

- `10G` → Go to line 10

- `H` → First visible line (high)

- `M` → Middle visible line

- `L` → Last visible line


### 8. **Scrolling & Positioning**

- `zz` → Center screen on cursor line

- `zt` → Top of screen

- `zb` → Bottom of screen

- `Ctrl+e` → Scroll down

- `Ctrl+y` → Scroll up


### 9. **Brackets & Matching**

- `%` → Jump between matching braces/brackets/parentheses

- `[ {` → Jump to opening brace

- `] }` → Jump to closing brace

- `[ (` → Opening parenthesis

- `] )` → Closing parenthesis


### 10. **Searching**

- `/word` → Forward search

- `?word` → Backward search

- `n` → Next result

- `N` → Previous result

- `*` → Search word under cursor


### 11. **Jump List**

- `Ctrl+o` → Go back

- `Ctrl+i` → Go forward

### 12. **Insert & Append**

- `i` → Insert before cursor

- `a` → Insert after cursor (append)

- `A` → Insert at end of line

- `o` → Open new line below

- `O` → Open new line above

- `u` → Undo

- `Ctrl+r` → Redo

### 13. **Operators**

- `y` → Yank (copy)

- `d` → Delete (also yanks)

- `c` → Change (delete + insert)

- `dd` → Delete whole line

- `yy` → Yank whole line

- `D` → Delete to end of line

- `C` → Change to end of line

- `p` → Paste after cursor

- `P` → Paste before cursor

- `.` → Repeat last change

### 14. **Visual Mode**

- `v` → Visual mode (select text)

- Apply operator (`d`, `y`, `c`) on selection

- `Esc` → Exit visual mode

- `o` → Jump between start/end of selection

### 15. **Search & Replace**

- `:%s/old/new/g` → Replace all

- `:%s/old/new/gc` → Replace all with confirmation


### 16. **Text Objects**

- `iw` / `aw` → Inner/around word

- `ip` / `ap` → Inner/around paragraph

- `i"` / `a"` → Inner/around double quotes

- `i'` / `a'` → Inner/around single quotes

- `i(`/`a(` or `i)`/`a)` → Inner/around parentheses

- `i{`/`a{` → Inner/around braces

- `i[`/`a[` → Inner/around brackets

- `it` / `at` → Inner/around tag


# Cheatsheet

---

## One-Page Vim Cheat Sheet (Textual Version)

### 1. **Modes & File Operations**

- `Esc` — Return to **Normal** (command) mode
    
- `i` — Insert before cursor
    
- `a` — Insert (append) after cursor
    
- `I` — Insert at beginning of line
    
- `A` — Insert at end of line
    
- `o` — Open new line **below** and enter Insert
    
- `O` — Open new line **above** and enter Insert
    
- `:w` — Save (write) file
    
- `:q` — Quit (fails if unsaved changes exist)
    
- `:wq` or `:x` — Save and quit
    
- `:q!` — Quit **without saving**
    

_(Inspired by multiple cheat sheet sources) ([josean.com](https://www.josean.com/posts/vim-essentials-cheatsheet?utm_source=chatgpt.com "Vim Essentials Cheatsheet & Guide"), [vimsheet.com](https://vimsheet.com/?utm_source=chatgpt.com "A Great Vim Cheat Sheet"), [Stanford University](https://web.stanford.edu/class/cs110/summer-2021/handouts/vim-cheat-sheet/?utm_source=chatgpt.com "Vim cheat sheet"))_

---

### 2. **Cursor & Screen Navigation**

**Basic (HJKL as arrow keys):**

- `h` — Left
    
- `j` — Down
    
- `k` — Up
    
- `l` — Right
    

**Line-based movements:**

- `0` — Start of line
    
- `^` — First non-blank character
    
- `$` — End of line
    
- `g_` — Last non-blank character ([vim.rtorr.com](https://vim.rtorr.com/?utm_source=chatgpt.com "Vim Cheat Sheet"), [Pluralsight](https://www.pluralsight.com/resources/blog/cloud/a-vim-cheat-sheet-reference-guide?utm_source=chatgpt.com "The Ultimate Vim Command Cheat Sheet"))
    

**Word-wise:**

- `w` / `b` — Next/previous word
    
- `W` / `B` — Word considering punctuation
    
- `e` / `E` — End of word/WORD ([vimsheet.com](https://vimsheet.com/?utm_source=chatgpt.com "A Great Vim Cheat Sheet"), [vim.rtorr.com](https://vim.rtorr.com/?utm_source=chatgpt.com "Vim Cheat Sheet"), [Medium](https://medium.com/%40sasidharan01/the-ultimate-vim-cheat-sheet-essential-commands-for-faster-editing-9cb4e4defd95?utm_source=chatgpt.com "The Ultimate Vim Cheat Sheet: Essential Commands for ..."))
    

**Paragraphs & lines:**

- `{` / `}` — Previous/next paragraph
    
- `gg` / `G` — First/last line of document
    
- `5G` or `5gg` — Go to line 5
    
- `H`, `M`, `L` — First / middle / last _visible_ screen line ([vim.rtorr.com](https://vim.rtorr.com/?utm_source=chatgpt.com "Vim Cheat Sheet"), [vimsheet.com](https://vimsheet.com/?utm_source=chatgpt.com "A Great Vim Cheat Sheet"), [Medium](https://medium.com/%40sasidharan01/the-ultimate-vim-cheat-sheet-essential-commands-for-faster-editing-9cb4e4defd95?utm_source=chatgpt.com "The Ultimate Vim Cheat Sheet: Essential Commands for ..."))
    

**Scrolling:**

- `Ctrl+f` / `Ctrl+b` — Screen forward/back a full page
    
- `Ctrl+d` / `Ctrl+u` — Half-page scroll down/up
    
- `Ctrl+e` / `Ctrl+y` — Scroll window _without moving cursor_
    
- `zz`, `zt`, `zb` — Center / top / bottom the cursor line in view ([vim.rtorr.com](https://vim.rtorr.com/?utm_source=chatgpt.com "Vim Cheat Sheet"), [Medium](https://medium.com/%40sasidharan01/the-ultimate-vim-cheat-sheet-essential-commands-for-faster-editing-9cb4e4defd95?utm_source=chatgpt.com "The Ultimate Vim Cheat Sheet: Essential Commands for ..."))
    

---

### 3. **Character Searching**

- `f<char>` — Find next `<char>` on the current line
    
- `F<char>` — Find previous `<char>`
    
- `t<char>` — Move just **before** next `<char>`
    
- `T<char>` — Move just **before** previous `<char>`
    
- `;` — Repeat last _f/F/t/T_ forward
    
- `,` — Repeat last _f/F/t/T_ backward ([vim.rtorr.com](https://vim.rtorr.com/?utm_source=chatgpt.com "Vim Cheat Sheet"), [josean.com](https://www.josean.com/posts/vim-essentials-cheatsheet?utm_source=chatgpt.com "Vim Essentials Cheatsheet & Guide"))
    

---

### 4. **Matching & Tags**

- `%` — Jump to matching brace, bracket, or parenthesis
    
- `[ {`, `] }` — Jump to opening/closing brace
    
- Matching within parentheses similarly with `[` `(` and `] )` ([Stanford University](https://web.stanford.edu/class/cs110/summer-2021/handouts/vim-cheat-sheet/?utm_source=chatgpt.com "Vim cheat sheet"))
    

---

### 5. **Editing (Operators & Commands)**

**Cut/Copy/Paste:**

- `d{motion}` — Delete (cuts) text covered by motion
    
- `y{motion}` — Yank (copy) text covered by motion
    
- `dd` / `yy` — Delete / Yank a whole line
    
- `D` / `Y` — Delete / Yank from cursor to end of line
    
- `p` / `P` — Paste after / before cursor ([vim.rtorr.com](https://vim.rtorr.com/?utm_source=chatgpt.com "Vim Cheat Sheet"), [Stanford University](https://web.stanford.edu/class/cs110/summer-2021/handouts/vim-cheat-sheet/?utm_source=chatgpt.com "Vim cheat sheet"), [Devhints.io cheatsheets](https://devhints.io/vim?utm_source=chatgpt.com "Vim cheatsheet"), [josean.com](https://www.josean.com/posts/vim-essentials-cheatsheet?utm_source=chatgpt.com "Vim Essentials Cheatsheet & Guide"))
    

**Change (Edit) Commands:**

- `c{motion}` — Delete then enter Insert mode
    
- `cc` — Change (delete) entire line and insert
    
- `C` — Change from cursor to end of line ([vimsheet.com](https://vimsheet.com/?utm_source=chatgpt.com "A Great Vim Cheat Sheet"), [Medium](https://medium.com/%40sasidharan01/the-ultimate-vim-cheat-sheet-essential-commands-for-faster-editing-9cb4e4defd95?utm_source=chatgpt.com "The Ultimate Vim Cheat Sheet: Essential Commands for ..."))
    

**Repeat & Undo/Redo:**

- `.` — Repeat last change
    
- `u` — Undo
    
- `Ctrl+r` — Redo ([Stanford University](https://web.stanford.edu/class/cs110/summer-2021/handouts/vim-cheat-sheet/?utm_source=chatgpt.com "Vim cheat sheet"), [vimsheet.com](https://vimsheet.com/?utm_source=chatgpt.com "A Great Vim Cheat Sheet"), [Medium](https://medium.com/%40sasidharan01/the-ultimate-vim-cheat-sheet-essential-commands-for-faster-editing-9cb4e4defd95?utm_source=chatgpt.com "The Ultimate Vim Cheat Sheet: Essential Commands for ..."))
    

---

### 6. **Visual Modes**

- `v` — Visual mode (select)
    
- `V` — Linewise visual mode
    
- `Ctrl+v` — Block visual mode
    
- After selection, apply `d`, `y`, `c`, etc.
    
- `Esc` — Exit visual mode
    
- `o` — Jump between start and end of selected block ([Stanford University](https://web.stanford.edu/class/cs110/summer-2021/handouts/vim-cheat-sheet/?utm_source=chatgpt.com "Vim cheat sheet"), [vimsheet.com](https://vimsheet.com/?utm_source=chatgpt.com "A Great Vim Cheat Sheet"), [josean.com](https://www.josean.com/posts/vim-essentials-cheatsheet?utm_source=chatgpt.com "Vim Essentials Cheatsheet & Guide"))
    

---

### 7. **Search & Replace**

- `/pattern` — Search forward
    
- `?pattern` — Search backward
    
- `n` / `N` — Next / previous search result
    
- `*` — Search forward for word under cursor
    
- `:%s/old/new/g` — Replace all in file
    
- `:%s/old/new/gc` — Replace all with **confirmation** ([Stanford University](https://web.stanford.edu/class/cs110/summer-2021/handouts/vim-cheat-sheet/?utm_source=chatgpt.com "Vim cheat sheet"), [vimsheet.com](https://vimsheet.com/?utm_source=chatgpt.com "A Great Vim Cheat Sheet"), [Medium](https://medium.com/%40sasidharan01/the-ultimate-vim-cheat-sheet-essential-commands-for-faster-editing-9cb4e4defd95?utm_source=chatgpt.com "The Ultimate Vim Cheat Sheet: Essential Commands for ..."))
    

---

### 8. **Jump List & History**

- `:jumps` — Show jump history
    
- `Ctrl+o` — Jump **back** to previous location
    
- `Ctrl+i` — Jump **forward** in history ([vim.rtorr.com](https://vim.rtorr.com/?utm_source=chatgpt.com "Vim Cheat Sheet"), [Stanford University](https://web.stanford.edu/class/cs110/summer-2021/handouts/vim-cheat-sheet/?utm_source=chatgpt.com "Vim cheat sheet"))
    

---

### 9. **Text Objects**

- `iw` / `aw` — Inner / around word
    
- `i"` / `a"` — Inner / around double quotes
    
- Similar for single quotes, parentheses, braces, brackets
    
- `it` / `at` — Inner / around tag
    
- Combined with `d`, `y`, `c`, etc., they provide powerful operations
    
- In Visual mode, use `o` to toggle between start/end of selection ([Stanford University](https://web.stanford.edu/class/cs110/summer-2021/handouts/vim-cheat-sheet/?utm_source=chatgpt.com "Vim cheat sheet"), [Medium](https://medium.com/%40sasidharan01/the-ultimate-vim-cheat-sheet-essential-commands-for-faster-editing-9cb4e4defd95?utm_source=chatgpt.com "The Ultimate Vim Cheat Sheet: Essential Commands for ..."), [josean.com](https://www.josean.com/posts/vim-essentials-cheatsheet?utm_source=chatgpt.com "Vim Essentials Cheatsheet & Guide"))
    

---

## Quick Guide Summary (One-Liner Reference)

```mysql
---------------------------------------------------
- Modes: Esc, i/a/I/A, o/O 
- Move: h j k l, 0 $ ^ w b W B e E gg G, H M L 
- Search: / ? n N * 
- Edit: d y c + motions, dd yy, D Y, p P 
- Visual: v V Ctrl+v + ops 
- Replace: :%s/old/new/gc 
- Undo/Redo: u Ctrl+r 
- Repeat: . 
- Jump: Ctrl+o/i 
- Match: % 
- TextObjects: iw aw i" a", it at
---------------------------------------------------
```

---

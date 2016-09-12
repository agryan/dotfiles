set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()

" let Vundle manage Vundle, required
Plugin 'gmarik/Vundle.vim'

" Color schemes
Plugin 'flazz/vim-colorschemes'
Plugin 'kristiandupont/shades-of-teal'

" Syntax checkers
Plugin 'scrooloose/syntastic'
let g:syntastic_check_on_open = 1
let g:syntastic_python_checkers = ['pep8', 'pylint', 'python']

" Jedi-vim
Plugin 'davidhalter/jedi-vim'
let g:jedi#show_call_signatures = ""
let g:jedi#popup_on_dot = 0

" Ctrl-P
Plugin 'kien/ctrlp.vim'

" Snippets
Plugin 'MarcWeber/vim-addon-mw-utils'
Plugin 'tomtom/tlib_vim'
Plugin 'garbas/vim-snipmate'
Plugin 'honza/vim-snippets'

" Python
Plugin 'hynek/vim-python-pep8-indent'

" HTML
Plugin 'mattn/emmet-vim'

" Rust
Plugin 'rust-lang/rust.vim'

" Repeat
Plugin 'tpope/vim-repeat'

" Surround
Plugin 'tpope/vim-surround'

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate

" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line
"
" Standard indent to be 4 spaces
" set tabstop=4
" set shiftwidth=4
" set expandtab

" Set 256 colors
set t_Co=256
colorscheme github

" Auto-source vimrc on save
autocmd bufwritepost .vimrc source $MYVIMRC

" Auto-test python code on save
function! TestPython ()
    :!python -m unittest discover -b
    call getchar() " Wait for terminal input before proceeding
endfunction

" Auto-write test_*.py files with pylint header
function! TemplatePython()
    if match(expand('%'), 'test_.*\.py') != -1
	" Test suite Python file
        r ~/vim/test_skeleton.py
        :normal! kdd
    else
	" Normal Python file
        :normal! gg6i"
	:normal! 03l
	:startinsert
    endif
endfunction

augroup python
    autocmd!
    autocmd BufNewFile *.py :call TemplatePython()
    autocmd BufWritePost *.py :call TestPython()
augroup END

" Auto-write *.py files with docstring
"augroup docpy
"    autocmd!
"    autocmd BufNewFile *.py :normal! gg6i"
"    autocmd BufNewFile *.py :normal! 03l
"    autocmd BufNewFile *.py :startinsert
"augroup END

"augroup testpy
"    autocmd!
"    autocmd BufNewFile test_*.py r ~/vim/test_skeleton.py
"    autocmd BufNewFile test_*.py :normal! kdd
"    \" autocmd BufNewFile test_*.py :1/"//g " remove module docstring
"augroup END

augroup web
    autocmd!
    autocmd Filetype javascript setlocal ts=4 sts=4 sw=4
    autocmd Filetype css setlocal ts=4 sts=4 sw=4
    autocmd Filetype html setlocal ts=4 sts=4 sw=4
augroup END

augroup clang
    autocmd!
    autocmd Filetype c setlocal ts=4 sts=4 sw=4
augroup END

" return to open new line in Esc mode
nmap <S-Enter> O<Esc>j
nmap <CR> o<Esc>k

" highlight search
set hlsearch

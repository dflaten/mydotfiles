"Set compatability due to requirement with vim-force plugin
set nocompatible
"syntax highlighting
syntax on
"indent properly if the filtype is known
if has("autocmd")
  filetype indent plugin on
endif
"line numbers on
set number
"Backspace over everything
set backspace=indent,eol,start
"define number of colors
set t_Co=256
" define initial background (light/dark)
set background=dark
" define color scheme
colorscheme solarized
" always display status line
set laststatus=2
" do not show mode as lightline shows it
set noshowmode
" define lightline configuration
let g:lightline = {
      \ 'colorscheme': 'solarized',
      \  'active': {
      \   'left': [ [ 'mode', 'paste' ],
      \             [ 'gitbranch', 'readonly', 'modified', 'buffers']
      \           ]   
      \ },
      \ 'component_function': {
      \   'gitbranch': 'fugitive#head',
      \ },
      \ }
" define function to toggle solarized theme
" change background and update lightline color scheme
function! ToggleSolarizedTheme()
  let &background = ( &background == "dark"? "light" : "dark" )
  if exists("g:lightline")
    runtime autoload/lightline/colorscheme/solarized.vim
    call lightline#colorscheme()
  endif
endfunction
" map F12 to ToggleSolarizedTheme() function
map <F12> :call ToggleSolarizedTheme()<CR>
"make insert -> Normal fast
set timeoutlen=1000 ttimeoutlen=0
"hidden buffers
set hidden
"make vimdiff use patience algorithm for diffs
set diffopt=internal,algorithm:patience,indent-heuristic
"Force.com settings
let g:apex_backup_folder="/Users/dflaten/tmp/apex/backup"
let g:apex_temp_folder="/Users/dflaten/tmp/apex/gvim-deployment"
"Credentials for the Salesforce org go in the directory below
let g:apex_properties_folder="/Users/dflaten/tmp/apex/gvim-deployment"
"Path to a package that is needed
let g:apex_tooling_force_dot_com_path="/Users/dflaten/tmp/apex/tooling-force.com-0.4.4.0.jar"
" Enable fzf
set rtp+=/usr/local/opt/fzf
"shortcut key for copy entire file to clipboard 
noremap ,, :%w !pbcopy<CR>
"settings for lightline-bufferline
let g:lightline.tabline          = {'left': [['buffers']], 'right':[['']]}
let g:lightline.component_expand = {'buffers': 'lightline#bufferline#buffers'}
let g:lightline.component_type   = {'buffers': 'tabsel'}
let g:lightline#bufferline#show_number = 1
"abreviation for finding files in parent folder usage: :e %%/
cabbr <expr> %% expand('%:p:h')
"highlight search  by default
set hlsearch
noremap ,; :set hlsearch!<CR>
"search, ignore case by default
set ignorecase
"if search has upper be case sensitive otherwise not
set smartcase
"move to search as you type
set incsearch
"Tidy command for HTML5
:vmap ,x :!tidy -q -i --show-errors 0<CR>
" REQUIRED. This makes vim invoke Latex-Suite when you open a tex file.
filetype plugin on
" OPTIONAL: Starting with Vim 7, the filetype of empty .tex files defaults to
" 'plaintex' instead of 'tex', which results in vim-latex not being loaded.
" The following changes the default filetype back to 'tex':
let g:tex_flavor='latex'
"setting filetype for typesetting
let g:Tex_CompileRule_pdf = 'xelatex'
"hotkey to update help pages
nmap ,j :helptags ~/.vim/doc<CR>
"rpmose mode, use 'call WordProcessor() to activate'
func! WordProcessor()
  " movement changes
  map j gj
  map k gk
  " formatting text
  setlocal formatoptions=1
  setlocal noexpandtab
  setlocal wrap
  setlocal linebreak
  " spelling and thesaurus
  setlocal spell spelllang=en_us
  set thesaurus+=/home/test/.vim/thesaurus/mthesaur.txt
  " complete+=s makes autocompletion search the thesaurus
  set complete+=s
endfu
com! WP call WordProcessor()
"Run Python script from VIM
nnoremap <buffer> <F9> :exec '!python3' shellescape(@%, 1)<cr>
"Run Python tests from VIM
nnoremap <buffer> <F8> :exec '!pytest' shellescape(@%, 1)<cr>
"Easier Split navigations
nnoremap <C-J> <C-W><C-J>
nnoremap <C-K> <C-W><C-K>
nnoremap <C-L> <C-W><C-L>
nnoremap <C-H> <C-W><C-H>
"Execute anonymous Apex
nnoremap <buffer> <F7> :exec '!sfdx force:apex:execute -f ' shellescape(@%, 1)<cr>
"Set apex code defaults, 4 spaces for tabs
autocmd FileType apexcode setlocal shiftwidth=4 tabstop=4
"set vcs to git
let g:signify_vcs_list = [ 'git' ]
highlight SignColumn ctermbg=073642
"toggle spell check
:command SC :setlocal spell! spelllang=en_us
"search for selection
vnoremap // y/<C-R>"<CR>
"java settings
func! JavaSettings()
  set path=**
  "chdir your/project/root "update this based on project
  "highlight functions using java guidelines
  let java_highlight_functions="style"
  "use below if people in project aren't following guidelines
  "let java_highlight_functions="indent"
  "System.out.println() and System.err.println() highlighted diff for debug.
  let java_highlight_debug=1
  "Take care of indents for Java.
  set autoindent
  set si
  set shiftwidth=4
  let java_highlight_functions = 1
  let java_highlight_all = 1
  " If you are trying this at runtime, you need to reload the syntax file
  set filetype=java
endfu
autocmd FileType java call JavaSettings() 

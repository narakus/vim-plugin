##### golang , neovim install

```shell
wget https://dl.google.com/go/go1.11.1.linux-amd64.tar.gz
tar -C /usr/local -xzf go1.11.1.linux-amd64.tar.gz

mkdir /usr/local/gocode 

# 添加到/etc/profile
export GOROOT=/usr/local/go
export GOBIN=$GOROOT/bin
export PATH=$PATH:$GOBIN

#set work directory
export GOPATH=/usr/local/gocode
export PATH=$PATH:${GOPATH//://bin:}/bin

source /etc/profile

```

##### neovim install

```shell
# centos7
yum -y install epel-release
curl -o /etc/yum.repos.d/dperson-neovim-epel-7.repo https://copr.fedorainfracloud.org/coprs/dperson/neovim/repo/epel-7/dperson-neovim-epel-7.repo 
yum -y install neovim

# debian
sudo apt-get install neovim
sudo apt-get install python-neovim
sudo apt-get install python3-neovim
```



##### neovim configure

```shell
curl -fLo ~/.local/share/nvim/site/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

yum install python2-pip python34-pip -y 
pip install neovim
pip3 install neovim

```



##### #~/.config/nvim

```neovim
" Specify a directory for plugins
" - For Neovim: ~/.local/share/nvim/plugged
" - Avoid using standard Vim directory names like 'plugin'
call plug#begin('~/.local/share/nvim/plugged')

" Make sure you use single quotes

" 好看的状态栏
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'

" 符号对齐
Plug 'junegunn/vim-easy-align'

" HTML
Plug 'mattn/emmet-vim'

" 括号匹配
Plug 'jiangmiao/auto-pairs'

" Any valid git URL is allowed
Plug 'https://github.com/junegunn/vim-github-dashboard.git'

Plug 'Shougo/deoplete.nvim', { 'do': ':UpdateRemotePlugins'  }
let g:deoplete#enable_at_startup = 1

" Multiple Plug commands can be written in a single line using | separators
Plug 'SirVer/ultisnips' | Plug 'honza/vim-snippets'

" On-demand loading
Plug 'scrooloose/nerdtree', { 'on':  'NERDTreeToggle' }
Plug 'tpope/vim-fireplace', { 'for': 'clojure' }

" Using a non-master branch
" Plug 'rdnetto/YCM-Generator', { 'branch': 'stable' }

" Using a tagged release; wildcard allowed (requires git 1.9.2 or above)
" Plug 'fatih/vim-go', { 'tag': '*' }

Plug 'fatih/vim-go', { 'do': ':GoUpdateBinaries'  }

" Plugin options
Plug 'nsf/gocode', { 'tag': 'v.20150303', 'rtp': 'vim' }

" Plugin outside ~/.vim/plugged with post-update hook
Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }

" Unmanaged plugin (manually installed and updated)
" Plug '~/my-prototype-plugin'

" python
Plug 'zchee/deoplete-jedi'

" golang
Plug 'nsf/gocode', { 'rtp': 'nvim', 'do': '/usr/local/gocode/src/github.com/mdempsky/gocode/nvim/symlink.sh'  }

" Initialize plugin system
call plug#end()
syntax enable
set ts=4
set expandtab
set autoindent
" set cursorline

let g:go_version_warning = 0
```

`打开nvim后执行 :PlugInstall`

https://golang.org/doc/install?download=go1.11.1.linux-amd64.tar.gz

https://github.com/neovim/neovim/wiki/Installing-Neovim

https://github.com/junegunn/vim-plug

# How to configure in ubuntu


**__src from : https://launchpad.net/ubuntu/saucy/+source/vim__**

__First__ of all you must use root permission

Open a __terminal__:
> $cd

- The lib of VIM Build dependencies

> $apt-get install debhelper dpkg-dev libacl1-dev libgnomeui-dev \
> libgpmg1-dev libgtk2.0-dev liblua5.2-dev libperl-dev libselinux1-dev \
> libtinfo-dev libxaw7-dev libxpm-dev libxt-dev lua5.2 python-dev ruby ruby-dev tcl-dev

- Get vim

> $hg clone https://vim.googlecode.com/hg/ vim

> $cd vim

- Enable support

> $./configure --with-features=huge \
>              --disable-darwin \
>              --disable-selinux \
>              --enable-luainterp \
>              --enable-perlinterp \
>              --enable-pythoninterp \
>              --enable-python3interp \
>              --enable-tclinterp \
>              --enable-rubyinterp \
>              --enable-cscope \
>              --enable-multibyte \
>              --enable-xim \
>              --enable-fontset \
>              --enable-gui=gnome2
              
- Vimrc should be use git

> $apt-get install git

- Copy vimrc to ".vimrc"

> $vim .vimrc


> $cd ~/.vim/bundle/neocomplete.vim/plugin/

> $vim neocomplete.vim

- replace "('lua') && ( (v:version == 703 && has('patch885')) )" to :

> ('lua') && ( (v:version == 703 && has('patch885')) || v:version >= 704 )

- some error with python when ":wq" the .py:

> Vim: Caught deadly signal ABRT
> sys.excepthook is missing
> lost sys.stderr
> sys.excepthook is missing
> lost sys.stderr
> Vim: Finished.

---
icon : note
---
# Install tmux on Shared Hosting

## Create Required Folder
1. mkdir -p $HOME/local

## Install libevent
1. Download libevent-stable from [https://github.com/libevent/libevent/releases](https://github.com/libevent/libevent/releases)
2. Extract
3. run `./configure --prefix=$HOME/local --disable-shared`
4. run `make`
5. run `make install`

## Install ncurses
1. Download ncurses stable from [https://invisible-island.net/ncurses/](https://invisible-island.net/ncurses/)
2. Extract
3. run `./configure --prefix=$HOME/local`
4. run `make`
5. run `make install`

## Install tmux
1. Download tmux from [https://github.com/tmux/tmux/releases](https://github.com/tmux/tmux/releases)
2. Extract
3. run 
```
./configure CFLAGS="-I$HOME/local/include -I$HOME/local/include/ncurses" LDFLAGS="-L$HOME/local/lib -L$HOME/local/include/ncurses -L$HOME/local/include"
```

4. run 
```
CPPFLAGS="-I$HOME/local/include -I$HOME/local/include/ncurses" LDFLAGS="-static -L$HOME/local/include -L$HOME/local/include/ncurses -L$HOME/local/lib" make
```

5. `cp tmux $HOME/local/bin`

Special Thanks to [ryin](https://gist.github.com/ryin/3106801)

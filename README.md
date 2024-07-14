# My Linux Config Files
Install oh-my-zsh
```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
Clone and symlink dotfiles
```sh
cd
git clone https://github.com/carlmon/dotfiles.git
ln -s -f dotfiles/.gitconfig
ln -s -f dotfiles/.hushfile
ln -s -f dotfiles/.tmux/.tmux.conf
ln -s -f dotfiles/.tmux/.tmux.conf.local
mv .zshrc{,_orig}
ln -s -f dotfiles/.zshrc
ln -s -d ~/dotfiles/.config/nvim .config/nvim
```
Install SauceCodeProNerdFont
```sh 
ln -s -d dotfiles/.fonts .fonts
fc-cache -v
```
Build and install neovim
```sh
sudo apt install -y ninja-build gettext libtool libtool-bin autoconf automake cmake g++ pkg-config unzip curl doxygen plocate luarocks ripgrep
git clone https://github.com/neovim/neovim && cd neovim && make CMAKE_BUILD_TYPE=RelWithDebInfo && sudo make install
```

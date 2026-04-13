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
ln -s -f dotfiles/.vimrc
```
Install SauceCodeProNerdFont
```sh 
ln -s -d dotfiles/.fonts .fonts
fc-cache -v
```
Install fnm and Node
```sh 
curl -fsSL https://fnm.vercel.app/install | bash
# Install Node 24
fnm use --install-if-missing 24
```
Install Poetry
```sh
pip install pipx
pipx install poetry
mkdir $ZSH_CUSTOM/plugins/poetry
poetry completions zsh > $ZSH_CUSTOM/plugins/poetry/_poetry
```

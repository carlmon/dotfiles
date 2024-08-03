# Basic Linux Config
## 
* Fish, fisher and Starship
```sh
sudo chsh -s /usr/bin/fish $USER
curl -sL https://raw.githubusercontent.com/jorgebucaran/fisher/main/functions/fisher.fish | source && fisher install jorgebucaran/fisher
curl -sS https://starship.rs/install.sh | sh
```
* Clone and symlink or copy dotfiles
```sh
git clone https://github.com/carlmon/dotfiles.git
ln -s dotfiles/.gitconfig "/home/$USER/.gitconfig"
ln -s dotfiles/.hushfile "/home/$USER/.hushfile"
ln -s dotfiles/.vimrc "/home/$USER/.vimrc"
mkdir -p ~/.config/fish
cp -r dotfiles/.config/fish/conf.d ~/.config/fish
```
* apt-fast
```sh
sudo add-apt-repository ppa:apt-fast/stable
sudo apt-get update
sudo apt-get -y install apt-fast
```
* Other utilities
```sh
sudo apt-fast install -y fzf fd-find bat jq git curl wget ripgrep
```
## Fonts
* SauceCodeProNerdFont
```sh 
ln -s -d dotfiles/.fonts .fonts
fc-cache -v
```
## Dev Environments
* fnm and Node
```sh 
curl -fsSL https://fnm.vercel.app/install | bash
# Install Node 24
fnm use --install-if-missing 24
```
* Poetry
```sh
sudo apt-fast install -y pipx
pipx install poetry
mkdir -p ~/.config/fish/completions
poetry completions fish > ~/.config/fish/completions/poetry.fish
```
* Kubectl
```sh
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x ./kubectl
mv ./kubectl ~/.local/bin
mkdir -p ~/.config/fish/completions
kubectl completion fish > ~/.config/fish/completions/kubectl.fish
```
* Go
```sh
set GO_DISTRO "go1.26.6.linux-amd64.tar.gz"
wget "https://go.dev/dl/$GO_DISTRO"
sudo rm -rf /usr/local/go && sudo tar -C /usr/local -xzf $GO_DISTRO
rm $GO_DISTRO
```
* Rust
```sh
curl -sSf https://sh.rustup.rs | sh
```
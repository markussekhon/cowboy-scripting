# nvim v0.10.3 on Debian 12 vm

NOTICE: WORK IN PROGRESS

steps to follow, hopefully it works for you Trison. 
Ill probably add this to the debian setup confluence page if it does.

I would recommend making a temp folder and running your commands in there,
there will be some left over tar files and/or zip files...
You can just nuke the folder after youre done installing everything :)

Assumptions: For the moment the assumption is 
you're Trison and attempting to get nvim up and running

Install Dependencies
```
sudo apt update
sudo apt remove nvim
sudo apt install -y ripgrep unzip build-essential libreadline-dev curl lua5.1 liblua5.1-0-dev
```

Install Stylua
```
wget https://github.com/JohnnyMorganz/StyLua/releases/download/v2.0.2/stylua-linux-x86_64.zip
unzip stylua-linux-x86_64.zip
chmod +x stylua
sudo mv stylua /usr/local/bin/
```

Install LuaRock
```
wget https://luarocks.github.io/luarocks/releases/luarocks-3.9.2.tar.gz
tar zxpf luarocks-3.9.2.tar.gz
cd luarocks-3.9.2
./configure --lua-version=5.1 --with-lua-include=/usr/include/lua5.1
make
sudo make install
```

Install Neovim
```
wget https://github.com/neovim/neovim/releases/download/v0.10.0/nvim-linux64.tar.gz
tar xzvf nvim-linux64.tar.gz
sudo mv nvim-linux64 /usr/local/
sudo ln -sf /usr/local/nvim-linux64/bin/nvim /usr/bin/nvim
```

Install Packer
```
git clone --depth 1 https://github.com/wbthomason/packer.nvim ~/.local/share/nvim/site/pack/packer/start/packer.nvim
```

At this point, I would launch Neovim...

If youre not prompted to install the packages I would suggest running `:Lazy` and installing them.

To check health it is simply `:checkhealth`

Ensure clangd is installed as an lsp using `:Mason`

Im currently working on figuring out how to make sure that when `:LspInfo` is called in root of libdfsi, it points to compile_commands.json 

:) Yeehaw~!


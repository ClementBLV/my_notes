
# Install Conda

good doc on the installation and how to swich with several distribution [here](https://olejorik.github.io/post/juliawsl/) 

```
sudo apt-get update
sudo apt-get install wget
wget https://repo.anaconda.com/miniconda/Miniconda3-py39_4.12.0-Linux-x86_64.sh

```

To check if the file has been download use 
```
 sha256sum Miniconda3-py39_4.12.0-Linux-x86_64.sh 
```
If a no such file occurs it means it hasn't been download

Restart the wsl to lunch it 

to uninstall it : 
```
rm -rf ~/.condarc ~/.conda ~/.continuum
rm -rf ~/miniconda
```

# Install Jupiter: 
```
pip install jupyterlab
pip install notebook
pip install black
```

# Install vs code 

installer sur CScode les plugin WSL , Remote devcelopper, remote explorer 
```
sudo apt update
sudo apt upgrade
sudo apt-get install nodejs
sudo apt install npm
go in the file type code .
(only once npm install  )
npm install
```

full info [here](https://code.visualstudio.com/docs/remote/wsl) or [here](https://ubuntu.com/tutorials/working-with-visual-studio-code-on-ubuntu-on-wsl2#6-creating-a-basic-web-server)

# Install julia 
```
wget https://julialang-s3.julialang.org/bin/linux/x64/1.5/julia-1.5.2-linux-x86_64.tar.gz
```
check the installation with 
```
sha256sum julia-1.5.2-linux-x86_64.tar.gz
```

unzip and install
```
tar -xvzf julia-1.5.2-linux-x86_64.tar.gz
sudo cp -r julia-1.5.2 /opt/
sudo ln -s /opt/julia-1.5.2/bin/julia /usr/local/bin/julia
```



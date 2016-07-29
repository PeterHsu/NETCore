CentOS 7 安裝手冊 for ASP.Net Core
-------------------------------------
1. Git
------------------------------------
```
$ sudo yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel gcc perl-ExtUtils-MakeMaker
$ sudo yum remove git
$ curl -sSL -o git.tar.gz https://www.kernel.org/pub/software/scm/git/git-2.9.2.tar.gz
$ sudo mkdir -p /usr/src/git
$ sudo tar zxf git.tar.gz -C /usr/src/git --strip 1
$ rm git.tar.gz
$ sudo make -C /usr/src/git prefix=/opt/git all
$ sudo make -C /usr/src/git prefix=/opt/git install
$ sudo ln -s /opt/git/bin/git /usr/bin
$ sudo rm -r /usr/src/git
```
2. Node
-------------------------------------------------
```
$ curl -sSL -o node.tar.xz https://nodejs.org/dist/v6.3.1/node-v6.3.1-linux-x64.tar.xz
$ sudo mkdir -p /opt/node
$ sudo tar Jxf node.tar.xz -C /opt/node --strip 1
$ rm node.tar.xz
$ echo "export PATH=$PATH:/opt/node/bin" | sudo tee --append /etc/bashrc
$ source /etc/bashrc
$ sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}
```
3. .NET Core
----------------------------------------------------
```
$ sudo yum install libunwind libicu
$ curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?LinkID=809131
$ sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
$ rm dotnet.tar.gz
$ sudo ln -s /opt/dotnet/dotnet /usr/bin
```
4. yeoman
-------------------------------------------------------
```
$ npm install -g yo bower grunt-cli gulp
$ npm install -g generator-aspnet
```
5. Visual Studio Code
--------------------------------------------------------
```
$ curl -sSL -o vscode.rpm http://go.microsoft.com/fwlink/?LinkID=760867
$ sudo yum install vscode.rpm
$ rm vscode.rpm
# 安裝所需的Plug in
```
6. 開發
-----------------------------------------------------------
```
$ mkdir src
$ cd src
$ yo aspnet
# 選Empty Web Application, 輸入EmptyWeb1
$ cd EmptyWeb1
$ dotnet restore
$ dotnet build
$ dotnet run
# 瀏覽http://localhost:5000
```

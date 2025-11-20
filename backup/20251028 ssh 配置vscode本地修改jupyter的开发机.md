## 文件同步，可以直接编写 
### 1.vscode安装ssh插件 remote-SSH

 ```shell
ssh # 检查是否安装了ssh

```
### 2.开发机创建ssh
开发机创建ssh ，名称随便填写
百度检索ip将ip地址设置为白名单，后面加上/24作为掩码
### 3. vscode创建密钥对
在cmd中输入

```
ssh-keygen
```
出现结果：

```
Generating public/private ed25519 key pair.
Enter file in which to save the key (C:\Users\Administrator/.ssh/id_ed25519):
```

### 4..进入这个文件ed25519.pub 文件中

```
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIJ7VQofGtnZi5ZJl9wF0Mx7p8Kms4WrYN0+8ttlCrCox administrator@DESKTOP-SL4G7T4
```
 
### 5. vscode里面进行配置

```
#~/.ssh/config
Host Ai-train-01
    HostName 106.63.100.63
    User batchcom
    Port 30060
    IdentityFile ~/.ssh/id_ed25519 
```
identityFile 可以用绝对路径

### 6.直接点击vscode下面的 ssh就可以连接了
+ linux
+ yes

## 直接运行调用，弥补开发机无法直接运行缺点
### 1.点击File—>Preferences—>Settings，搜索Show Login Terminal，并勾选Always reveal the SSH login terminal
### 2. 运行命令
直接点击上方的 运行 按钮运行
```shell
Ctrl+Shift+P (Windows/Linux) 或 Cmd+Shift+P (Mac)
Python: Select Interpreter
```
cd到命令行采用下面的方式运行

```shell
python demo.py
```

## 运行jupyter notebook 文件
在vscode里面的terminal里面进行下面的操作

```shell
conda activate python2.5.1
pip install jupyter
conda install ipykernel
python -m ipykernel install --user --name python2.5.1 --display-name "python251"

```

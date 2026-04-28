##  linux 下 python 版本和位置查看
- which python #查找系统中有那些python
- ls /usr/bin/python* # 列出所有的python文件
- ls /usr/bin/python* # 系统python版本查看
- conda --version # 查看conda的安装版本
- conda info # conda 的信息
- conda env list # 列出conda的所有env
- conda list python # 查看当前的python版本
- conda create -n aidd310 python=3.10

## linux 下conda创建新的环境
- ls -la /home/ # 检查用户主目录的权限
- conda create -p ./conda_envs/aidd310 python=3.10 # 当前文件夹创建conda_envs 存储一个aidd310 的env名称，指定python版本是310
- conda activate ./conda_envs/aidd310 # 激活aidd310
```shell
mkdir /home/dataset-assist-0/conda-env
mkdir /home/dataset-assist-0/conda-pkg
conda config --add envs_dirs /home/dataset-assist-0/conda-env/
conda config --add pkgs_dirs /home/dataset-assist-0/conda-pkg/
conda create -n myenv python=3.11
``` 
- conda deactivate # 退出当前环境
- rm -rf /home/dataset-assist-0/tmp/zsl/conda_envs/aidd310 文件夹中的环境
- conda create -p /home/dataset-assist-0/tmp/zsl/conda_envs/aidd310 python=3.10 -y 重新安装环境
- python --version # 查看当前python环境

## windows 上的pkg打包到linux
windows上导出pkg
- 脏的方式：conda env export > environment.yml
- 干净的方式: conda env export --no-builds > environment.yml
linux 上安装pkg
- conda activate aidd310 # 激活新的环境
- conda activate /home/dataset-assist-0/tmp/zsl/conda_envs/aidd310

```shell
# 添加清华镜像
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes

# 然后重新安装
conda install numpy=1.26.4 scipy pandas matplotlib -y
``` 
- pip install numpy==1.26.4 pandas matplotlib scipy
- pip install openbabel-wheel
- pip install pybel
- pip install rdkit==2025.9.1
- 

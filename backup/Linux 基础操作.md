# Linux 基础操作
##  进入命令
- cd +Tab 自动补全
- cd 后退到home
- cd .. 后退一格
- cd ../ 后退两格
- cd / 后退到根目录
- pwd 当前所处文件的绝对路径

## 展示命令
- ls 全部罗列
- ls |head 列出部分数据
- ls |head -n 100 列出100条数据
- ls |wc -l 列出文件夹中一共有多少个文件
- head -n1 .chag 显示.chag的第一行数据

## 简单计算
- total_charge=$(echo "$protein_charge+$ligand_charge"|bc) 表示浮点数运算，bc可以用来处理浮点数
- sed 可以对文本进行查找、替换、删除
- sed -i "1s/.*/$total_charge/" .chrg 在第一行进行操作 ，.*表示匹配整行 $total_charge 替换为总电荷值，.chrg表示应用在这个文件上
- 注意如果total_charge 是 -1 会报错
- 可以更换为其他分割符 sed -i "1s#.*#$total_charge# .CHRG"
```shell
    sed -i "1s#.*#$total_charge#" .CHRG # 对第一行进行整体替代
    sed -i "$s#$#$ligand_charge#" .CHRG # $匹配模式是行尾
```

## 文件操作
- pwd 输出当前的文件夹路径
- cp A B 将A 的文件复制到B 中
- cp A/* B 复制A 中的所有文件到A 中
- rm -rf data 删除文件
### 解压文件
1. tar
```shell
- tar -xzvf name.tar.gz|head-100  解压出来，看看100个
- tar -xzvf name.tar.gz 直接解压
```
2.7zip
```shell 
- sudo apt update
- sudo apt install p7zip-full #7z安装
- 7z x 01_ligand_process.7z # 解压7z文件
- 7z x 01_ligand_process.7z -o/path/to/destination # 解压到指定目录
- 7z l 01_ligand_process.7z # 列出压缩包的内容
- 7z t 01_ligand_process.7z # 测试压缩包的完整性
```
3.zip
```shell 
- zip -r data5k.zip /database 将database文件夹压缩到data5k.zip
- unzip name.zip
- unzip data.zip -d /home/user/extracted/ #解压到指定目录
- unzip -l archive.zip #查看压缩包的内容
```

- ls | head -100 | xargs -I {} cp {} /home/user/destination/ 复制100个到xargs管道中，并到文件夹 （复制文件）
- ls | head -5000 | xargs -I {} cp -r "{}" /home/dataset-assist-0/tmp/zsl/0-database 直接复制文件夹 需要-r

 - ls |head -1000|xargs -I {} cp {} /home/dataset-assist-0/tmp/zsl/GatorAffinity-DB/GatorAffinity-DB-Fixed


## 查看命令
- df -h /home/dataset 查看当前文件的磁盘容量


## 行动命令
- ctrl c 中止当前操作
- kill %1 中断当前序号为1 的项目
- kill %$(jobs -p) 中断所有的项目
- ctrl z 暂停当前操作

## 基础函数操作
- echo "my script begin to run!" # 打印函数
- python 命令行输入：
```powershell
local pdbid=$1 #读取命令行输入，注意没有空格
python myscrip.py\
--ligandfile "$ligandfile"\
``` 
- python 的引用
python 同文件夹下的.py
python \home\tmp\zsl\全文件下的.py

ls | head -5000 | while read -r item; do
    cp -r "$item" /home/dataset-assist-0/tmp/zsl/0-database
done

## 调用函数的方式
- 定义函数：01_ligand_process() { } # 大括号前需要空格
- chmod +x your_script.sh #给脚本增加权限
- ./your_script.sh # 直接运行
- cat 01_ligand_data.txt | parallel --joblog 02.log --retries 3 --jobs 16 01_ligand_process {} # 最后面的大括号前面需要空格
- base_directory=$(pwd)
# 基本配置
- 安装GNU parallel
sudo apt-get install parallel  # Ubuntu/Debian
- 安装文件转化
sudo apt install dos2unix
dos2unix mydoc.txt
## 单文件txt操作
- cp 01_ligand_data.txt 01_ligand_data.txt.backup #备份原文件
- sed -i 's/[[:space:]]//g' 01_ligand_data.txt # 移除所有空白字符（空格、制表符）
- cat 01_ligand_data.txt | head -10 #列出来清理之后的操作
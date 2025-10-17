# Linux 基础操作
## 1. 进入命令
- cd +Tab 自动补全
- cd 后退到home
- cd .. 后退一格
- cd ../ 后退两格
- cd / 后退到根目录

## 展示命令
- ls 全部罗列
- ls |head 列出部分数据
- ls |head -n 100 列出100条数据
- ls |wc -l 列出文件夹中一共有多少个文件

## 文件操作
- pwd 输出当前的文件夹路径
- cp A B 将A 的文件复制到B 中
- cp A/* B 复制A 中的所有文件到A 中
- ls | head -100 | xargs -I {} cp {} /home/user/destination/ 复制100个到xargs管道中，并到文件夹 （复制文件）
- ls | head -5000 | xargs -I {} cp -r "{}" /home/dataset-assist-0/tmp/zsl/0-database 直接复制文件夹 需要-r

 ls |head -1000|xargs -I {} cp {} /home/dataset-assist-0/tmp/zsl/GatorAffinity-DB/GatorAffinity-DB-Fixed
## 行动命令
- ctrl c 中止当前操作
- kill %1 中断当前序号为1 的项目
- kill %$(jobs -p) 中断所有的项目
- ctrl z 暂停当前操作

## 基础函数操作

ls | head -5000 | while read -r item; do
    cp -r "$item" /home/dataset-assist-0/tmp/zsl/0-database
done
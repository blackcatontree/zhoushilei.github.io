 Get-ChildItem -Directory | Select-Object Name | Out-File -FilePath folder_list.txt -Encoding UTF8 
将当前文件夹中的所有文件夹的名字复制到一个文件中，并且将其放置在该文件夹下 编码方式采用UTF8的方式
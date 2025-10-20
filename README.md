# thesixonenine-scoop-bucket

## Append *.ps1 Scripts

1. 新增文件下载 wget 命令(git-scripts.yml)
2. 修改 hash 值为当前版本(将 git-scripts.json 中的 hash 替换到 git-scripts.yml 的 sed 命令中)
3. 修改 git 标签为准备发布的版本, 全局搜索替换(git-scripts.yml, git-scripts.json)
4. 新增 bin 命令(git-scripts.json)
5. 提交代码, 执行 Action

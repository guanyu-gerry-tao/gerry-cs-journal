# Bash - 终端语言

**Bash（命令行）** 语言，Bash 是 macOS（以及 Linux）默认的 Shell 之一。它用于在终端中管理文件、运行程序、控制 Git 版本、安装软件等。

- **终端（iTerm2 / Terminal.app）就是一个 Bash（或 Zsh）环境**，可以输入命令来操作文件、运行 Python、管理 Git。
- **你不需要学得很深入**，只要掌握 **基本命令**，就能高效管理你的代码。

## **📌 1. 终端导航（文件和目录操作）**

| **命令** | **缩写含义** | **用途** | **示例** |
| --- | --- | --- | --- |
| `pwd` | **Print Working Directory** | 显示当前目录路径 | `pwd` |
| `ls` | **List** | 列出当前目录的文件 | `ls` |
| `ls -lah` | **List -long -all -human** | 显示详细信息（包括隐藏文件） | `ls -lah` |
| `cd` | **Change Directory** | 切换到指定目录 | `cd ~/Developer/` |
| `cd ..` | **Change Directory Up** | 返回上一级目录 | `cd ..` |
| `cd -` | **Change Directory (Previous)** | 返回上一次访问的目录 | `cd -` |
| `mkdir` | **Make Directory** | 创建新文件夹 | `mkdir my-folder` |
| `rm -r` | **Remove -recursive** | 递归删除文件夹及其内容 | `rm -r my-folder` |
| `rmdir` | **Remove Directory** | 仅删除空文件夹 | `rmdir empty-folder` |
| `mv` | **Move** | 移动或**重命名**文件 | `mv old.txt new.txt`
`mv old_file.txt ~/Documents/new_file.txt` |
| `cp` | **Copy** | 复制文件或文件夹 | `cp file1.txt file2.txt` |

## **📌 2. 文件管理**

| **命令** | **缩写含义** | **用途** | **示例** |
| --- | --- | --- | --- |
| `touch` | **Create Empty File** | 创建一个空文件 | `touch myfile.txt` |
| `nano` | **Nano Editor** | 用 Nano 终端编辑器打开文件 | `nano myfile.txt` |
| `cat` | **Concatenate** | 显示文件内容 | `cat myfile.txt` |
| `less` | **View Large File** | 分页查看大文件内容 | `less largefile.txt` |
| `head` | **Show First Lines** | 显示文件的前 10 行 | `head myfile.txt` |
| `tail` | **Show Last Lines** | 显示文件的最后 10 行 | `tail myfile.txt` |
| `echo` | **Print to Terminal** | 在终端打印文本 | `echo "Hello World"` |
| `chmod` | **Change Mode** | 修改文件权限 | `chmod +x script.sh` |
| `chown` | **Change Owner** | 修改文件所有者 | `chown user:group file.txt` |

## **📌 3. 进程管理**

| **命令** | **缩写含义** | **用途** | **示例** |
| --- | --- | --- | --- |
| `ps` | **Process Status** | 查看当前运行的进程 | `ps aux` |
| `top` | **Top Processes** | 实时查看系统资源占用 | `top` |
| `kill` | **Kill Process** | 终止进程 | `kill 1234` |
| `kill -9` | **Force Kill** | 强制终止进程 | `kill -9 1234` |
| `pkill` | **Process Kill** | 按进程名称终止 | `pkill python` |

## **📌 4. 磁盘管理**

| **命令** | **缩写含义** | **用途** | **示例** |
| --- | --- | --- | --- |
| `df -h` | **Disk Free -human readable** | 显示磁盘使用情况 | `df -h` |
| `du -sh` | **Disk Usage -summary -human** | 显示文件夹大小 | `du -sh ~/Downloads` |

## **📌 5. Git 版本管理**

| **命令** | **缩写含义** | **用途** | **示例** |
| --- | --- | --- | --- |
| `git clone` | **Git Clone** | 从 GitHub 克隆仓库 | `git clone https://github.com/user/repo.git` |
| `git status` | **Git Status** | 显示当前 Git 仓库状态 | `git status` |
| `git add .` | **Git Add** | 添加所有修改到 Git 暂存区 | `git add .` |
| `git commit -m` | **Git Commit Message** | 提交更改 | `git commit -m "✨ 新功能"` |
| `git push origin main` | **Git Push** | 推送代码到 GitHub | `git push origin main` |
| `git pull origin main` | **Git Pull** | 拉取最新代码 | `git pull origin main` |

## **📌 6. 搜索 & 文本处理**

| **命令** | **缩写含义** | **用途** | **示例** |
| --- | --- | --- | --- |
| `grep` | **Global Regular Expression Print** | 在文件中搜索关键字 | `grep "error" logfile.txt` |
| `find` | **Find Files** | 查找文件 | `find ~/Documents -name "*.txt"` |
| `sed` | **Stream Editor** | 替换文件内容 | `sed 's/old/new/g' file.txt` |
| `awk` | **Text Processing** | 文本处理 | `awk '{print $1}' file.txt` |

## **📌 7. 网络管理**

| **命令** | **缩写含义** | **用途** | **示例** |
| --- | --- | --- | --- |
| `ping` | **Check Network Connection** | 测试网络连接 | `ping google.com` |
| `curl` | **Client URL** | 获取网页内容 | `curl https://example.com` |
| `wget` | **Web Get** | 下载文件 | `wget https://example.com/file.zip` |
| `ifconfig` | **Interface Configuration** | 查看网络接口信息 | `ifconfig` |
| `netstat -an` | **Network Status** | 查看网络连接 | `netstat -an` |

## **📌 8. 终端快捷键**

| **快捷键** | **用途** |
| --- | --- |
| `Ctrl + A` | 光标移动到行首 |
| `Ctrl + E` | 光标移动到行尾 |
| `Ctrl + U` | 删除当前输入行 |
| `Ctrl + K` | 删除光标后面的内容 |
| `Ctrl + C` | 终止当前运行的命令 |
| `Ctrl + D` | 退出终端 |
| `Ctrl + R` | 搜索历史命令 |
| `Tab` | 自动补全文件或命令 |
| `Cmd + T` | 在 iTerm2 中打开新标签页 |
| `Cmd + D` | 在 iTerm2 中左右分屏 |

## **📌 1. 为什么要用 Bash？**

| **特点** | **Finder（GUI 操作）** | **Bash（命令行操作）** |
| --- | --- | --- |
| **批量操作** | 需要手动点击多个文件 | 一行命令可完成（如 `mv *.jpg new-folder/`） |
| **Git 版本管理** | Finder 不能直接管理 Git | Git 命令全都在 Bash 里运行 |
| **远程服务器管理** | Finder 无法连接服务器 | `ssh my-server` 轻松远程管理 |
| **运行 Python 代码** | 需要打开 Python 解释器 | 直接输入 `python3 script.py` |
| **自动化任务** | 需要手动操作 | `for` 循环批量处理文件 |
| **精确文件管理** | 只能看文件名 | `ls -lah` 查看权限、大小、修改时间 |
| **文本处理** | 只能手动编辑 | `grep`、`awk`、`sed` 可快速搜索替换 |
| **历史命令** | 不能记录你做过的操作 | `history` 命令可以回溯所有操作 |
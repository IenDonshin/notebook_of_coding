# Git 与 GitHub 常用命令行总结

## 1. 基本配置

### 初始化和配置
```bash
# 初始化 Git 仓库 / Gitリポジトリを初期化 / Initialize a Git repository
git init
# 设置用户名 / ユーザー名を設定 / Set username
git config --global user.name "你的名字" 
# 设置邮箱 / メールアドレスを設定 / Set email address
git config --global user.email "你的邮箱"
# 查看当前配置 / 現在の設定を表示 / View current configuration
git config --list            
```

## 2.创建与克隆

### 创建本地仓库
```bash
# 初始化 Git 仓库 / Gitリポジトリを初期化 / Initialize a Git repository
git init
```
### 克隆远程仓库
```bash
# 克隆远程仓库到本地 / リモートリポジトリをローカルにクローン / Clone remote repository to local
git clone [url]

# 克隆指定分支 / 指定されたブランチをクローン / Clone a specific branch
git clone -b [branch] [url]
```
## 3.分支管理
### 查看与创建分支
```bash
# 查看本地分支 / ローカルブランチを表示 / View local branches
git branch

# 查看远程分支 / リモートブランチを表示 / View remote branches
git branch -r

# 创建新分支 / 新しいブランチを作成 / Create a new branch
git branch [branch-name]

```

### 切换与删除分支
```bash
# 切换到指定分支 / 指定されたブランチに切り替え / Switch to the specified branch
git checkout [branch-name]

# 创建并切换到新分支 / 新しいブランチを作成して切り替え / Create and switch to a new branch
git checkout -b [branch-name]

# 删除本地分支 / ローカルブランチを削除 / Delete a local branch
git branch -d [branch-name]

# 删除远程分支 / リモートブランチを削除 / Delete a remote branch
git push origin --delete [branch-name]

```

## 4.提交与修改
### 添加和提交
```bash
# 添加指定文件到暂存区 / 指定したファイルをステージに追加 / Add a specific file to the staging area
git add [file]

# 添加所有更改到暂存区 / 全ての変更をステージに追加 / Add all changes to the staging area
git add .

# 提交更改到本地仓库 / ローカルリポジトリに変更をコミット / Commit changes to the local repository
git commit -m "描述信息"

# 修改上一次提交信息 / 前回のコミットメッセージを修正 / Amend the previous commit message
git commit --amend

```
### 查看状态和历史
```bash
# 查看当前状态 / 現在のステータスを表示 / View the current status
git status

# 查看提交日志 / コミットログを表示 / View the commit log
git log

# 简洁模式查看日志 / 簡潔な形式でログを表示 / View the log in a concise format
git log --oneline

# 查看未暂存的改动 / ステージされていない変更を表示 / View unstaged changes
git diff

# 查看已暂存的改动 / ステージされた変更を表示 / View staged changes
git diff --staged

```

## 5.同步操作
### 连接远程仓库
```bash
# 添加远程仓库 / リモートリポジトリを追加 / Add a remote repository
git remote add origin [url]

# 查看远程仓库 / リモートリポジトリを表示 / View remote repositories
git remote -v
```
### 推送和拉取
```bash
# 推送到远程分支 / リモートブランチにプッシュ / Push to the remote branch
git push origin [branch-name]

# 关联本地分支与远程分支并推送 / ローカルブランチをリモートブランチと関連付けてプッシュ / Link local branch to remote and push
git push -u origin [branch-name]

# 拉取远程更新并合并 / リモートの更新を取得してマージ / Pull remote updates and merge
git pull

# 拉取远程更新但不合并 / リモートの更新を取得するだけでマージはしない / Fetch remote updates without merging
git fetch
```

## 6.合并与冲突
### 分支合并
```bash
# 合并指定分支到当前分支 / 指定したブランチを現在のブランチにマージ / Merge a specified branch into the current branch
git merge [branch-name]
```
### 解决冲突
```bash
# 解决冲突后添加到暂存区 / 衝突を解決してステージに追加 / Add resolved conflict files to the staging area
git add [file]

# 解决冲突后提交 / 衝突解消後にコミット / Commit after resolving conflicts
git commit -m "解决冲突"
```
## 7.标签管理
### 创建与操作标签
```bash
# 查看所有标签 / 全てのタグを表示 / View all tags
git tag

# 创建标签 / タグを作成 / Create a tag
git tag [tag-name]

# 创建带信息的标签 / メッセージ付きタグを作成 / Create a tag with a message
git tag -a [tag-name] -m "描述信息"

# 推送标签到远程仓库 / タグをリモートリポジトリにプッシュ / Push a tag to the remote repository
git push origin [tag-name]

# 推送所有标签到远程仓库 / 全てのタグをリモートリポジトリにプッシュ / Push all tags to the remote repository
git push origin --tags

# 删除本地标签 / ローカルタグを削除 / Delete a local tag
git tag -d [tag-name]

# 删除远程标签 / リモートタグを削除 / Delete a remote tag
git push origin --delete [tag-name]
```

## 8.撤销与回滚
### 撤销更改
```bash
# 撤销工作区改动 / 作業領域の変更を取り消し / Discard changes in the working directory
git checkout -- [file]

# 取消暂存的文件 / ステージからファイルを取り消し / Unstage a file
git reset HEAD [file]
```

### 回滚版本
```bash
# 回滚到某版本，保留改动 / あるバージョンに戻すが変更は保持 / Rollback to a version, keep changes
git reset --soft [commit-id]

# 回滚到某版本并清除改动 / あるバージョンに戻して変更を破棄 / Rollback to a version and discard changes
git reset --hard [commit-id]
```

## 9.GitHub相关操作
### SSH配置
#### 创建远程仓库
在GitHub上创建仓库
这里需要注意，如果本地有代码的话，那远程仓库最好是纯空白仓库，readme都不要有；或者远程创建好仓库之后再clone到本地
#### 添加远程仓库
```bash
# 添加远程仓库 / リモートリポジトリを追加 / Add a remote repository
git remote add origin [仓库地址]

# 推送本地代码到远程 / ローカルコードをリモートにプッシュ / Push local code to the remote repository
git push -u origin main
```

## 10.其他实用命令
```bash
# 清理未跟踪的文件 / トラッキングされていないファイルをクリーン / Clean untracked files
git clean -f

# 查看操作记录（包括已删除的分支） / 操作履歴を表示（削除されたブランチを含む） / View operation history (including deleted branches)
git reflog
```


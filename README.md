<div align="center">
  <h1>多人协作文档操作 Manual</h1>
  <a href="https://github.com/liyinred/Git_Wenhao/blob/main/1_eng.md" target="_blank" style="font-size: 18px;">English Version</a>
</div>

## Git 技术概览
Git 是分布式版本控制系统，适合多人协作、变更跟踪与历史管理。核心概念：分布式、快照、分支、提交与冲突解决。

### 核心概念（简要）
- 分布式版本控制：每台机器都有完整仓库和历史。
- 快照与提交：每次提交存储项目快照。
- 分支与合并：在分支上开发，合并或变基到主分支。
- 暂存区：准备提交的临时区域。
- 远程仓库：GitHub、GitLab 等用于共享与协作。

### 准备
- 安装 Git（例如 Windows 安装包）。
- 注册 GitHub 账户并设置 SSH 或 HTTPS 认证。
- 配置用户信息：
```bash
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱地址"
```

## 多人协作示例（精简步骤）
1. 邀请协作者
- 仓库管理员（Leader）在 Settings > Collaborators 邀请成员，成员在通知中接受邀请。

2. 克隆仓库
```bash
cd /path/to/workdir
git clone https://github.com/owner/Repo.git
cd Repo
```

3. 创建分支并编辑
```bash
git checkout -b feature/描述
# 编辑文件
git add 文件
git commit -m "描述性提交信息"
```

4. 推送分支
```bash
git push origin feature/描述
```

5. 发起 Pull Request（PR）
- 在 GitHub 上为分支创建 PR，填写清晰标题与描述，等待维护者审核并合并。

6. 同步主分支
合并后，其他成员更新本地：
```bash
git checkout main
git pull origin main
```

7. 变基（可选）
当需要把分支更新到最新主分支基础上：
```bash
git checkout feature/描述
git fetch origin
git rebase origin/main
# 若冲突，手动解决后
git add 冲突文件
git rebase --continue
# 变基后可能需要强推
git push --force-with-lease origin feature/描述
```

8. 查看历史与差异
```bash
git log --oneline
git log -p -- 路径/文件
git diff <commitA> <commitB>
git diff <commit>^ <commit>
```

9. 常见推送问题
- 若提示 failed to push，可能为分支不同步或认证问题：先 git pull 再 merge/rebase，再推送；检查远程 URL 与认证（SSH/HTTPS/代理）。

## 开发协作建议
- 分支命名和提交信息要规范（例如 feature/、fix/、chore/）。
- PR 描述列出变更要点与测试步骤。
- 使用 Code Review、CI 检查与合并策略（保护主分支）。

简化版旨在快速上手并覆盖关键协作流程。完整示例与图片资源保留在仓库其他位置（已移除 pic 目录图片引用）。

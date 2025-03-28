# RAKsmart 服务器重置 CentOS 7 系统 root 密码完整指南

CentOS 7 作为企业级 Linux 发行版，是 RAKsmart 服务器用户最常用的操作系统之一。但有时用户可能会遇到忘记 root 密码的情况，导致无法正常登录系统。本文将详细介绍如何通过单用户模式重置 CentOS 7 的 root 密码。

## 准备工作
- 确保您拥有 RAKsmart 服务器的物理或控制台访问权限
- 了解基本的 Linux 命令行操作
- 准备设置一个安全的新密码

👉 [【点击查看】2025年最新 Raksmart 优惠码及特价云服务器方案汇总](https://bit.ly/raksmart)

## 详细操作步骤

### 第一步：进入 GRUB 引导菜单
1. 重启您的 RAKsmart 服务器
2. 在系统启动时，快速按下 `Esc` 或 `E` 键进入 GRUB 引导菜单

### 第二步：修改内核参数
1. 在 GRUB 菜单中选择要启动的内核
2. 找到以 `linux16` 开头的行
3. 将 `ro` 参数改为 `rw`
4. 在行末添加 `init=/sysroot/bin/sh`

### 第三步：进入单用户模式
1. 按下 `Ctrl+X` 组合键
2. 系统将以单用户模式启动

### 第四步：挂载系统并修改密码
bash
chroot /sysroot
passwd

系统将提示您输入并确认新密码。请设置一个强密码以确保服务器安全。

### 第五步：更新 SELinux 配置
bash
touch /.autorelabel
exit
reboot

## 注意事项
- 此操作需要服务器重启
- 新密码建议包含大小写字母、数字和特殊字符
- 操作完成后请妥善保管新密码

通过以上步骤，您就可以成功重置 RAKsmart 服务器上 CentOS 7 系统的 root 密码。如果遇到任何问题，建议联系 RAKsmart 技术支持获取专业帮助。

> 提示：定期更改密码是保障服务器安全的重要措施之一
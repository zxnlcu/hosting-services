# 新手教程：使用游戏云VPS快速搭建Rust服务器

## 前言
本教程专为新手设计，采用最简化的操作步骤，帮助您快速搭建Rust游戏服务器。部分方案可能不是最优解，但能确保新手顺利完成部署。

## 服务器选购指南

### 省钱小技巧
1. 注册[雨云](https://bit.ly/RainYun)账户，使用优惠码"wp-admin"可获5元无门槛券
2. 完成账户验证（绑定手机/邮箱/社交账号）可获得大量积分
3. 积分可在积分商城兑换优惠券或增值服务

👉 [【点击查看】2025年最新雨云优惠码及特价云服务器方案汇总](https://bit.ly/RainYun)

### 初次配置建议
- **服务器类型**：VPS服务器-Gold 6146-入门级
- **系统选择**：推荐Debian（资源占用小）
- **存储配置**：建议30GB数据盘（支持大地图）
- **IP选择**：共享IP经济实惠，独享IP更稳定但费用较高

## 服务器部署步骤

### 1. 初始化设置
1. 选择1元试用方案（可提升用户等级）
2. 等待1-3分钟完成创建
3. 进入服务器管理界面

### 2. 端口配置
必须映射以下端口：
- 主端口：28015（默认）或自定义端口
- 可选端口：28016（备用）
- RCON端口：11520
- 查询端口：11521

### 3. 系统准备
bash
# 更新软件源
apt-get update

# 安装必要依赖
dpkg --add-architecture i386
apt install curl wget file tar bzip2 gzip unzip bsdmainutils python3 util-linux ca-certificates binutils bc jq tmux netcat lib32gcc-s1 lib32stdc++6 lib32z1

## Rust服务器安装

### 1. 创建专用用户
bash
adduser rustserver
su - rustserver

### 2. 安装LGSM管理工具
bash
wget -O linuxgsm.sh https://linuxgsm.sh && chmod +x linuxgsm.sh && bash linuxgsm.sh rustserver

### 3. 安装服务器
bash
./rustserver install

*注意：如遇依赖问题，需切换root用户补全依赖*

## 服务器配置

### 1. 基础配置
编辑配置文件：
bash
vi /home/rustserver/serverfiles/server/rustserver/cfg/server.cfg

关键参数：
- `server.port 28579`（需与映射端口一致）
- `server.name "你的服务器名"`
- `server.description "服务器描述"`

### 2. LGSM配置
bash
cd /home/rustserver/lgsm/config-lgsm/rustserver
cp _default.cfg rustserver.cfg
vi rustserver.cfg

配置建议：
- 设置RCON密码
- 开启RCON Web管理
- 指定游戏模式

## 启动服务器
bash
./rustserver start

## 进阶选项
- 安装Mod支持（可选）
- 配置自动备份
- 设置定时重启

*提示：完整教程持续更新中，建议收藏本页面*
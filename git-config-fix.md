# GitHub Desktop 连接问题解决方案

## 问题描述
`fatal: unable to access 'https://github.com/fayne-feng/fayne-feng.github.io.git/': Recv failure: Connection was reset`

## 解决方案

### 1. 立即解决方案

#### 重启GitHub Desktop
1. 完全关闭GitHub Desktop
2. 等待30秒
3. 重新启动GitHub Desktop
4. 尝试再次推送

#### 清除缓存
1. 关闭GitHub Desktop
2. 按 `Win + R`，输入 `%APPDATA%`
3. 删除 `GitHub Desktop` 文件夹
4. 重新启动GitHub Desktop

### 2. 网络配置解决方案

#### 检查防火墙
1. 打开Windows防火墙设置
2. 确保GitHub Desktop有网络访问权限
3. 临时关闭防火墙测试

#### 配置Git代理（如果需要）
```bash
# 设置HTTP代理
git config --global http.proxy http://proxy-server:port

# 设置HTTPS代理
git config --global https.proxy https://proxy-server:port

# 取消代理设置
git config --global --unset http.proxy
git config --global --unset https.proxy
```

#### 增加Git缓冲区大小
```bash
git config --global http.postBuffer 524288000
git config --global http.maxRequestBuffer 100M
git config --global core.compression 9
```

### 3. 高级解决方案

#### 使用SSH替代HTTPS
1. 生成SSH密钥
2. 添加到GitHub账户
3. 更改仓库远程URL为SSH

#### 更改DNS服务器
1. 使用Google DNS (8.8.8.8, 8.8.4.4)
2. 或使用Cloudflare DNS (1.1.1.1, 1.0.0.1)

### 4. 临时解决方案

#### 使用命令行Git
如果GitHub Desktop持续失败，可以：
1. 安装Git for Windows
2. 使用命令行进行推送：
```bash
git add .
git commit -m "Update files"
git push origin main
```

### 5. 检查清单

- [ ] 网络连接正常
- [ ] GitHub Desktop已重启
- [ ] 防火墙设置正确
- [ ] 代理设置正确（如果需要）
- [ ] Git配置正确
- [ ] 尝试使用命令行Git

### 6. 联系支持

如果问题持续存在：
1. 检查GitHub状态页面
2. 联系GitHub支持
3. 考虑使用VPN服务 
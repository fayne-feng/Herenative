# HereNative 域名配置指南

## 问题描述
用户反映无法通过 herenative.com 访问网站

## 解决方案

### 1. GitHub Pages 设置

#### 在GitHub仓库中设置：
1. 进入仓库设置 (Settings)
2. 点击 "Pages" 选项
3. 在 "Source" 部分选择 "Deploy from a branch"
4. 选择 "main" 分支
5. 在 "Custom domain" 中输入：`herenative.com`
6. 勾选 "Enforce HTTPS"
7. 点击 "Save"

### 2. DNS 配置

#### 在域名注册商处设置DNS记录：

**A记录：**
```
类型: A
名称: @
值: 185.199.108.153
TTL: 3600

类型: A
名称: @
值: 185.199.109.153
TTL: 3600

类型: A
名称: @
值: 185.199.110.153
TTL: 3600

类型: A
名称: @
值: 185.199.111.153
TTL: 3600
```

**CNAME记录：**
```
类型: CNAME
名称: www
值: fayne-feng.github.io
TTL: 3600
```

### 3. 验证配置

#### 检查DNS传播：
```bash
# 检查主域名
nslookup herenative.com

# 检查www子域名
nslookup www.herenative.com

# 检查GitHub Pages
nslookup fayne-feng.github.io
```

#### 检查HTTPS证书：
- 访问 https://herenative.com
- 确保显示绿色锁图标
- 检查证书是否由GitHub Pages提供

### 4. 常见问题解决

#### 问题1：DNS传播延迟
- 等待24-48小时让DNS完全传播
- 使用不同DNS服务器测试

#### 问题2：HTTPS证书问题
- 确保在GitHub Pages设置中启用了HTTPS
- 检查域名是否正确配置

#### 问题3：404错误
- 确保仓库中有index.html文件
- 检查CNAME文件内容是否正确

### 5. 测试步骤

1. **本地测试：**
   ```bash
   # 启动本地服务器
   python -m http.server 8000
   # 访问 http://localhost:8000
   ```

2. **在线测试：**
   - 访问 https://herenative.com
   - 访问 https://www.herenative.com
   - 检查所有页面是否正常加载

3. **移动端测试：**
   - 在手机浏览器中访问
   - 检查响应式设计是否正常

### 6. 监控和维护

#### 设置监控：
- 使用UptimeRobot监控网站可用性
- 设置SSL证书过期提醒
- 监控DNS解析状态

#### 定期检查：
- 每月检查DNS配置
- 确保GitHub Pages设置正确
- 更新SSL证书（自动）

### 7. 联系支持

如果问题持续存在：
1. 检查GitHub Pages状态：https://www.githubstatus.com/
2. 联系域名注册商技术支持
3. 检查GitHub Pages文档：https://docs.github.com/en/pages

## 当前配置状态

- ✅ CNAME文件已配置为 `herenative.com`
- ✅ .htaccess文件已更新
- ✅ 404页面已创建
- ✅ GitHub Actions工作流已配置
- ⏳ 等待DNS传播完成
- ⏳ 等待GitHub Pages设置生效 
# DNS配置修复指南 - 确保两个域名都正常工作

## 当前问题
- ✅ www.herenative.com 工作正常
- ❌ herenative.com 显示SSL证书问题

## 解决方案

### 1. 修复DNS配置

#### 在域名注册商控制面板中设置：

**A记录（主域名）：**
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

**CNAME记录（www子域名）：**
```
类型: CNAME
名称: www
值: fayne-feng.github.io
TTL: 3600
```

### 2. 删除错误的DNS记录

**必须删除的记录：**
- 删除指向 `192.64.119.56` 的A记录
- 删除任何指向其他IP的A记录

### 3. 验证DNS配置

#### 检查命令：
```bash
# 检查主域名
nslookup herenative.com 8.8.8.8

# 检查www子域名
nslookup www.herenative.com 8.8.8.8

# 应该只显示GitHub Pages的IP地址
```

### 4. GitHub Pages设置

#### 在GitHub仓库中：
1. 进入 Settings > Pages
2. 在 "Custom domain" 中输入：`herenative.com`
3. 勾选 "Enforce HTTPS"
4. 点击 "Save"

### 5. 等待DNS传播

- 通常需要15分钟到48小时
- 使用不同DNS服务器测试传播状态

## 预期结果

修复后应该：
- ✅ herenative.com 正常工作
- ✅ www.herenative.com 正常工作
- ✅ 两个域名都有正确的SSL证书
- ✅ 自动重定向到HTTPS

## 临时解决方案

在DNS修复期间，用户可以：
1. 使用 https://www.herenative.com
2. 使用 https://fayne-feng.github.io 
# PHP 验证工具类

一个轻量级的 PHP 验证工具类，用于验证 IP 地址、手机号、邮箱等常用功能。

## 特性

- 验证 IP 地址（IPv4/IPv6）
- 验证邮箱格式
- 检测手机设备访问
- 检测微信访问
- 验证手机号码格式
- 验证固定电话格式
- 检测 HTTPS 请求

## 项目结构

```
verify/
├── src/                    # 源代码
│   └── Verify.php         # 验证工具类
├── composer.json            # 依赖配置
├── composer.lock
└── README.md
```

## 安装

```bash
composer require chenbool/verify
```

## 使用方法

### 初始化

```php
use ChenBool\Verify;

$verify = new Verify();
```

### 验证 IP 地址

```php
// 判断是否为合法的 IP 地址
$ipv4 = $verify->isIPAddress('192.168.1.1');   // 返回 4
$ipv6 = $verify->isIPAddress('2001:0db8:85a3:0000:0000:8a2e:0370:7334'); // 返回 6
$invalid = $verify->isIPAddress('invalid');     // 返回 false
```

### 验证邮箱

```php
// 验证邮箱格式
$verify->isValidEmail('test@example.com');  // true
$verify->isValidEmail('invalid');            // false
```

### 检测客户端类型

```php
// 判断是否为手机访问
$verify->isMobile();  // true 或 false

// 判断是否为微信访问
$verify->isWeiXin();  // true 或 false

// 判断是否为 HTTPS 请求
$verify->isHttps();   // true 或 false
```

### 验证手机号码

```php
// 检查手机号码格式（中国大陆手机号）
$verify->checkMobile('13800138000');  // true
$verify->checkMobile('1234567890');    // false
```

### 验证固定电话

```php
// 检查固定电话格式
$verify->checkTelephone('010-12345678');  // true
$verify->checkTelephone('0571-12345678'); // true
$verify->checkTelephone('12345678');      // false
```

## API 说明

| 方法 | 说明 | 返回值 |
|------|------|--------|
| `isIPAddress($ip)` | 验证 IP 地址 | 4 (IPv4) / 6 (IPv6) / false |
| `isValidEmail($email)` | 验证邮箱格式 | true / false |
| `isMobile()` | 检测手机设备访问 | true / false |
| `isWeiXin()` | 检测微信访问 | true / false |
| `checkMobile($mobile)` | 验证手机号码 | true / false |
| `checkTelephone($tel)` | 验证固定电话 | true / false |
| `isHttps()` | 检测 HTTPS 请求 | true / false |

## 环境要求

- PHP >= 5.6.0

## 相关链接

- [PHP filter_var](https://www.php.net/manual/en/function.filter-var.php)
- [正则表达式手册](https://www.php.net/manual/en/book.pcre.php)

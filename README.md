# EDtunnel

<p align="center">
  <img src="https://raw.githubusercontent.com/6Kmfi6HP/EDtunnel/refs/heads/main/image/logo.png" alt="edgetunnel" style="margin-bottom: -50px;">
</p>

EDtunnel is a proxy tool based on Cloudflare Workers and Pages that supports multiple protocols and configuration options.

[![Repository](https://img.shields.io/badge/View%20on-GitHub-blue.svg)](https://github.com/6Kmfi6HP/EDtunnel)
[![Telegram](https://img.shields.io/badge/Discuss-Telegram-blue.svg)](https://t.me/edtunnel)

## Features

- Support for Cloudflare Workers and Pages deployment
- Multiple UUID configuration support
- Custom proxy IP and port support
- SOCKS5 proxy support
- Automatic configuration subscription link
- Simple and easy deployment process

## 🚀 Quick Deployment

### Deploy on Pages.dev

1. Watch deployment tutorial video：
   [YouTube Tutorial](https://www.youtube.com/watch?v=8I-yTNHB0aw)

2. Clone this repository and deploy in Cloudflare Pages

### Deploy on Worker.dev

1. Copy `_worker.js` code from [here](https://github.com/6Kmfi6HP/EDtunnel/blob/main/_worker.js)

2. Or click the button below to deploy directly:

   [![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/6Kmfi6HP/EDtunnel)

## ⚙️ Configuration Guide

### Environment Variables

| (Variable) | (Required) | (Example) | (Description) |
|------------------|-------------------|---------------|-------------------|
| `UUID` | (No) | (Single): `12345678-1234-1234-1234-123456789012`<br>(Multiple): `uuid1,uuid2,uuid3` | User identification |
| `PROXYIP` | (No) | `1.1.1.1` (or) `example.com`<br>(Multiple): `1.1.1.1:9443,2.2.2.2:8443` | Custom proxy IP and port |
| `SOCKS5` | (No) | `user:pass@host:port`<br>(Multiple): `user1:pass1@host1:port1,user2:pass2@host2:port2` | SOCKS5 proxy configuration |
| `SOCKS5_RELAY` | (No) | `true` (or) `false` | Enable SOCKS5 traffic relay |

### Non-443 Port Configuration

1. Visit `https://proxyip.edtunnel.best/`
2. Enter `ProxyIP:proxyport` and click Check
3. When showing `Proxy IP: true` it's available
4. Configure in Worker: `PROXYIP=211.230.110.231:50008`

Note: Proxy IPs with ports may not work on HTTP-only Cloudflare sites.

### UUID Configuration

#### Method 1
Set in `wrangler.toml` file (not recommended for public repositories)

```toml
[vars]
UUID = "your-uuid-here"
```

#### Method 2
Set in Cloudflare Dashboard environment variables (recommended method)

## ⚠️ Important Note: Multiple Configuration Separator

All multiple configurations MUST use English comma(,) as separator, NOT Chinese comma(，)

✅ Correct Examples:
```bash
# Multiple UUID
UUID=uuid1,uuid2,uuid3

# Multiple SOCKS5 proxies
SOCKS5=192.168.1.1:1080,192.168.1.2:1080

# Multiple PROXYIP
PROXYIP=1.1.1.1:443,2.2.2.2:443
```

❌ Wrong Examples:
```bash
# Wrong: Using Chinese comma
UUID=uuid1，uuid2，uuid3

# Wrong: Using Chinese comma
SOCKS5=192.168.1.1:1080，192.168.1.2:1080
```

## 📱 Quick Start

### Auto Configuration Subscribe

Use the following link for auto configuration:
```
https://sub.xf.free.hr/auto
```

### View Configuration

- Visit your domain: `https://your-domain.pages.dev`
- Use specific UUID: `/sub/[uuid]`
- View full configuration: visit domain root path
- Get subscription content: visit `/sub/[uuid]`

## 🔧 Advanced Configuration

### Multiple UUID Support

You can configure multiple UUIDs in these ways:

1. Via environment variables:
   ```
   UUID=uuid1,uuid2,uuid3
   ```

2. Via configuration file:
   ```toml
   [vars]
   UUID = "uuid1,uuid2,uuid3"
   ```

### SOCKS5 Proxy Configuration

Supports the following formats:
- Basic format: `host:port`
- Authentication format: `username:password@host:port`
- Multiple proxies (separated by English comma): `proxy1,proxy2,proxy3`

#### Configuration Examples:

1. Single Proxy:
```bash
# Basic format
SOCKS5=192.168.1.1:1080

# With authentication
SOCKS5=user:pass@192.168.1.1:1080
```

2. Multiple Proxies (separated by English comma):
```bash
# Multiple basic proxies
SOCKS5=192.168.1.1:1080,192.168.1.2:1080,192.168.1.3:1080

# Multiple proxies with authentication
SOCKS5=user1:pass1@host1:port1,user2:pass2@host2:port2

# Mixed format
SOCKS5=192.168.1.1:1080,user:pass@192.168.1.2:1080,192.168.1.3:1080
```

#### SOCKS5 Proxy Load Balancing

When multiple proxies are configured, the system will automatically perform load balancing:

- Random selection
- Automatic failover
- Support mixed authentication methods

#### SOCKS5_RELAY Settings

Enable SOCKS5 global relay:
```bash
SOCKS5_RELAY=true
```

Notes:
- Ensure proxy servers are stable and available
- Recommend using private proxies for better security
- Use commas to separate multiple proxies
- Support dynamic proxy addition and removal

## 🚨 Notes

- Proxy IPs with ports may not work on HTTP-only Cloudflare sites
- Use commas to separate multiple UUIDs
- Recommend setting sensitive information via environment variables
- Update regularly for latest features and security fixes

## 🔧 Environment Variable Settings

### Workers.dev Settings
Configure environment variables in Workers settings page
![workers](image/image-1.png)

### Pages.dev Settings
Configure environment variables in Pages settings page
![pages](image/image-2.png)

## 💬 Get Help

- Telegram Group: [EDtunnel Group](https://t.me/edtunnel)
- Repository: [EDtunnel](https://github.com/6Kmfi6HP/EDtunnel)
- Issue Report: [Create New Issue](https://github.com/6Kmfi6HP/EDtunnel/issues)
- Feature Request: [Submit Request](https://github.com/6Kmfi6HP/EDtunnel/discussions)

## 📝 Contributing

Welcome Pull Requests to improve the project! Please ensure:

1. Code follows project standards
2. Add necessary tests
3. Update relevant documentation
4. Clearly describe the reasons for changes

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

## Star History

<a href="https://star-history.com/#6Kmfi6HP/EDtunnel&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=6Kmfi6HP/EDtunnel&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=6Kmfi6HP/EDtunnel&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=6Kmfi6HP/EDtunnel&type=Date" />
  </picture>
</a>

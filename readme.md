# Sing-box 配置指南 (Hysteria2)

## 配置文件说明

- **`hysteria2.json`**：仅支持单一节点，不支持 `clashapi` 的配置，即无法切换 `rule`、`direct`、`global` 模式，默认使用 `tun` 和规则代理，仅使用少量规则集，可用于快速测试。
- **`hysteria2_selector.json`**：支持 `clashapi`，可以自由切换 `rule`、`direct`、`global` 模式，使用大量规则集，可用于平时使用。

请根据实际情况填写 `outbound` 字段中的内容。

> [!NOTE]
> 请注意 sing-box 1.11 版本不支持端口跳跃，所以没有 `server_ports` 字段。

## 配置模板

```json
{
    "type": "hysteria2",
    "tag": "Hysteria2 节点",
    "server": "你的服务器ip",
    "server_port": "你的服务器端口，可以不加引号例如直接填写443",
    "server_ports": [
        "如果开启了端口跳跃请填写,例如20000:50000,如果没有请删除"
    ],
    "up_mbps": "上行速率",
    "down_mbps": "下行速率",
    "password": "你的服务器密码",
    "tls": {
        "enabled": true,
        "server_name": "您的域名或服务器端使用的域名",
        "insecure": true
    }
}
```

## 填写示例

```json
{
    "type": "hysteria2",
    "tag": "Hysteria2 节点",
    "server": "123.123.123.123",
    "server_port": "443",
    "server_ports": [
        "20000:50000"
    ],
    "up_mbps": 20,
    "down_mbps": 50,
    "password": "123456",
    "tls": {
        "enabled": true,
        "server_name": "bing.com",
        "insecure": true
    }
}
```
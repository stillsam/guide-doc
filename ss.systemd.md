## Shadowsocks Systemd Service

Copy ssserver.service to `usr/lib/systemd/system/` and run:

`sudo systemctl enable ssserver`
`sudo systemctl start ssserver`
`sudo systemctl status ssserver`

the same usage to sslocal.service

### sslocal.service
```bash
[Unit]
Description=shadowsocks client
Wants=network-online.target
After=network.target

[Service]
Type=simple
ExecStart=/usr/bin/sslocal -c /home/kemon/shadowsocks.json

[Install]
WantedBy=multi-user.target
```

### ssserver.service
```bash
[Unit]
Description=shadowsocks server
After=network.target

[Service]
Type=simple
ExecStart=/usr/bin/ssserver -c /etc/shadowsocks.json

[Install]
WantedBy=multi-user.target
```

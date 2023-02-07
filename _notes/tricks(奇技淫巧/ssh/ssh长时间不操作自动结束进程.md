当长时间不使用ssh客户端时，客户端会断开与远程服务器的链接
`ssh -o ServerAliveInterval=60  root@8.142.28.241 `
本地 ssh 每隔 60s 向 server 端 sshd 发送 keep-alive 包
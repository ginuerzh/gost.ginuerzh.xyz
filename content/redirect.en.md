+++
date = "2017-11-20T13:03:15+08:00"
menu = "main"
title = "Transparent Proxy"
weight = 40
+++

GOST added support for TCP Transparent Proxy in version 2.3.

```bash
gost -L redirect://:12345 -F 192.168.1.1:1080
```

Together with iptables, global proxy can be achieved.

```
iptables -t nat -A OUTPUT -p tcp --match multiport ! --dports 12345,1080 -j DNAT --to-destination 127.0.0.1:12345
```

{{< admonition title="NOTE" type="warning" >}}
Transparent proxy supports only Linux system.
{{< /admonition >}}

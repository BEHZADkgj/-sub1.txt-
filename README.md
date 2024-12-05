{                                                               "route": {
                "geoip": {                                              "path": "geo-assets\\sagernet-sing-geoip-geoip.db"                                                              },
                "geosite": {                                            "path": "geo-assets\\sagernet-sing-geosite-geosite.db"                                                          },
                "rules": [                                              {
                        "inbound": "dns-in",                                    "outbound": "dns-out"
                },                                                      {
                        "port": 53,                                             "outbound": "dns-out"
                },                                                      {
                        "clash_mode": "Direct",                                 "outbound": "direct"
                },                                                      {
                        "clash_mode": "Global",                                 "outbound": "select"
                }                                                       ],
                "auto_detect_interface": true,                          "override_android_vpn": true
        },                                                      "outbounds": [
                {                                                       "type": "selector",
                "tag": "select",
                "outbounds": [
                        "auto",
                        "IP->Iran, kolandone",
                        "IP->Main, kolandone"
                ],
                "default": "auto"
                },
                {
                "type": "urltest",
                "tag": "auto",
                "outbounds": [
                        "IP->Iran, kolandone",
                        "IP->Main, kolandone"
                ],
                "url": "http://cp.cloudflare.com/",
                "interval": "10m0s"
                },
                {
                "type": "wireguard",
                "tag": "IP->Iran, kolandone",
                "local_address": [
                        "172.16.0.2/32",
                        ""
                ],
                "private_key": "",
                "server": "188.114.97.17",
                "server_port": 955,
                "peer_public_key": "bmXOC+F1FxEMF9dyiK2H5/1SUtzH0JuVo51h2wPfgyo=",
                "reserved": ,
                "mtu": 1280,
                "fake_packets": "5-10"
                },
                {
                "type": "wireguard",
                "tag": "IP->Main, kolandone",
                "detour": "IP->Iran, kolandone",
                "local_address": [
                        "172.16.0.2/32",
                        ""
                ],
                "private_key": "",
                "server": "188.114.97.17",
                "server_port": 955,
                "peer_public_key": "bmXOC+F1FxEMF9dyiK2H5/1SUtzH0JuVo51h2wPfgyo=",
                "reserved": ,
                "mtu": 1280,
                "fake_packets": "5-10"
                },
                {
                "type": "dns",
                "tag": "dns-out"
                },
                {
                "type": "direct",
                "tag": "direct"
                },
                {
                "type": "direct",
                "tag": "bypass"
                },
                {
                "type": "block",
                "tag": "block"
                }
        ]
        }
# producerjson

Producer JSON smart contract for Enu.

Enu 出块人描述文件

# Usage 用法

### json sample 描述文件例子

"node_type": "full":主要用于给用户提供api节点服务

"node_type": "seed":主要用于节点p2p连接


```json
{
    "producer_account_name": "enumivoqsxio",
    "org": {
        "candidate_name": "qsx.io",
        "website": "http://enumivo.qsx.io",
        "email": "x@qsx.io"
    },
    "social_network": {
        "github": "https://github.com/enu-zion",
        "telegram": "https://t.me/Joshuaqiu"
    },
    "nodes": [
        {
            "location": {
                "name": "Singapore",
                "country": "Singapore",
                "latitude": 1.18,
                "longitude": 103.51
            },
            "node_type": "full",
            "api_endpoint": "http://enu.qsx.io",
            "ssl_endpoint": "https://enu.qsx.io"
        },
        {
            "location": {
                "name": "Singapore",
                "country": "Singapore",
                "latitude": 1.18,
                "longitude": 103.51
            },
            "node_type": "seed",
            "p2p_endpoint": "seed.qsx.io:10876"
        }
    ]
}
```
save json in bp.json file.

将json格式的信息存在 bp.json 文件。

### Add to the table 添加节点信息

```
enucli push action producerjson set '{"owner":"enumivoqsxio", "json": "'`printf %q $(cat bp.json | tr -d "\r")`'"}' -p enumivoqsxio@active
```

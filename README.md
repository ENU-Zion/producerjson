# producerjson

Producer JSON smart contract for FIBOS.

FIBOS 出块人描述文件

# Usage 用法

### json sample 描述文件例子

"node_type": "full":主要用于给用户提供api节点服务

"node_type": "seed":主要用于节点p2p连接


```json
let producerjson = {
    "producer_account_name": "fibosrockskr",
    "org": {
        "candidate_name": "Fibos Rocks",
        "website": "http://fibos.rocks",
        "email": "support@fibos.rocks"
    },
    "nodes": [
        {
            "location": {
                "name": "Tokyo",
                "country": "JP",
                "latitude": 34.8,
                "longitude": 138.4
            },
            "node_type": "full",
            "api_endpoint": "http://api.fibos.rocks",
            "ssl_endpoint": "https://api.fibos.rocks"
        },
        {
            "location": {
                "name": "Tokyo",
                "country": "JP",
                "latitude": 34.8,
                "longitude": 138.4
            },
            "node_type": "producer"
        },
        {
            "location": {
                "name": "Tokyo",
                "country": "JP",
                "latitude": 34.8,
                "longitude": 138.4
            },
            "node_type": "seed",
            "p2p_endpoint": "seed.fibos.rocks:10100"
        }
    ]
}
```

### View the table 查看列表

```
var result = fibos.getTableRowsSync(true, "producerjson", "producerjson", "producerjson")
console.log(result);
```


### Add to the table 添加节点信息

```
var ctx = fibos.contractSync("producerjson");
var result = ctx.setSync({
    "owner": "fibosrockskr",
    "json": JSON.stringify(producerjson)
}, {
        "authorization": "fibosrockskr"
    })

console.log(result);
```

### Remove from the table 删除节点信息

```
var ctx = fibos.contractSync("producerjson");
var result = ctx.delSync({
    "owner": "fibosrockskr"
}, {
        "authorization": "fibosrockskr"
    })

console.log(result);
```


---

# How to build
```
./build.sh
```
or
```
eosiocpp -g producerjson.abi producerjson.cpp && eosiocpp -o producerjson.wast producerjson.cpp
```

# How to deploy

```
fibos.setabiSync('producerjson', fs.readFileSync(abipath));

fibos.setcodeSync('producerjson', 0, 0, fs.readFileSync(wasmpath));
```

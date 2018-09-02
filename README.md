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

# producerjson sample 例子
``` json
{
 "producer_account_name": "teamgreymass",
  "producer_public_key": "EOS4xurP5oZk4WvMUp9neKkw94DJ2iq48GtMD5Dff3GKe6krh2ctR",
  "org": {
    "candidate_name": "Greymass",
    "website": "https://greymass.com",
    "ownership_disclosure": "https://greymass.com/ownership_disclosure",
    "code_of_conduct": "https://greymass.com/code_of_conduct",
    "email":"hello@greymass.com",
    "branding":{
      "logo_256":"https://greymass.com/greymass_logo_256X256.png",
      "logo_1024":"https://greymass.com/greymass_logo_1024X1024.png",
      "logo_svg":"https://greymass.com/greymass_logo.svg"
    },
    "location": {
      "name": "Michigan",
      "country": "US",
      "latitude": 44.3148,
      "longitude": -85.6024
    },
    "social": {
      "steemit": "greymass",
      "twitter": "greymass",
      "youtube": "",
      "facebook": "",
      "github":"greymass",
      "reddit": "",
      "keybase": "team/greymass",
      "telegram": "",
      "wechat":""
    }
  },
  "nodes": [
    {
      "location": {
        "name": "CA",
        "country": "CA",
        "latitude": 45.3168,
        "longitude": -73.8659
      },
      "api_endpoint": "http://eos.greymass.com",
      "ssl_endpoint": "https://eos.greymass.com",
      "node_type" : "full"
    },
    {
      "location": {
        "name": "GB",
        "country": "GB",
        "latitude": 51.5142,
        "longitude": -0.0931
      },
      "node_type": "seed",
      "p2p_endpoint": "seed1.greymass.com:9876"
    },
    {
      "location": {
        "name": "US",
        "country": "US",
        "latitude": 32.7825,
        "longitude": -96.8207
      },
      "node_type": "seed",
      "p2p_endpoint": "seed2.greymass.com:9876"
    }
  ]
}
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

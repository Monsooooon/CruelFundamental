## 2022/10/20

### 如何将公钥从证书中取出？如何验证证书合法?

- 客户端使用内置的认证机构的公钥去解密公钥证书里的数字签名，得到数字指纹
- 客户端对公钥证书的服务器公钥进行数字摘要算法得到数字之分
- 比较两者是否一致
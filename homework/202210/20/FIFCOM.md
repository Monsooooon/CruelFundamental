## 2022/10/20

- 如何将公钥从证书中取出？如何验证证书合法?



首先客户端使用同样的Hash算法获取证书的Hash值，然后使用CA的公钥解密Certificate Signature内容，获取Hash值 ，如果两者的Hash值相等，那么证书可以信赖
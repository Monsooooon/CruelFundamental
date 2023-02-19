# 对称性加密跟非对称性加密的比较，使用场景

## 对称加密
对称加密又叫做私钥加密，即信息的发送方和接收方使用同一个密钥去加密和解密数据，对称加密的特点是算法公开，加密和解密速度快，1适合对大数据量进行加密

## 非对称加密

非对称加密也叫作公钥加密，非对称加密与对称加密相比，其安全性更好，对称加密的通信双方使用相同的密钥，如果密钥泄露，那么通信就会被破解，因此安全性相对比较差。而非对称加密使用一对密钥，公钥和私钥，二者成对出现，私钥自己保存，不能对外泄露，公钥任何人都可以获得

特点是加密和解密使用两个不同的密钥，私钥仅自己保存，安全性高缺点是加密和解密花费的时间很长，速度慢，只适合对少量数据进行加密
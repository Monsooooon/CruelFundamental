### 请简述RSA算法的加解密流程

- 生成密钥
  - 选择两个不相等的质数p q
  - 计算pq的乘积n
  - 计算欧拉函数 \phi(n) = (p-1)*(q-1)  计算出来 不大于n且与n互质的整数个数。（欧拉函数，对正整数n，欧拉函数是小于等于n的正整数中与n互质的数的数目）
  - 选择一个与\phi(n)互质的整数e，且1<e<\phi(n)
  - 计算e对\phi(n)的模反元素d。计算公式d*e==1(mod(n))
  - 公钥(n, e)，私钥(n,d)
  - 销毁p q
- 加解密流程
  - 加密：发送方向接收方发送明文消息m，发送方使用公钥(n, e)加密【m ^ e = c(mod n)】 m为整数 小于 n
  - 解密：接收方获取密文c，使用自己的私钥(n, d)解密 【c ^ d = m(mod n) 】



ref:https://www.cnblogs.com/richard-xiong/p/9923283.html
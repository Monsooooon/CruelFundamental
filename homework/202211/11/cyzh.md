## 2022/11/11

### 试述电子邮件收发的过程

- 发送人点击发送后， 发送邮件的工作就交给了用户代理，用户代理通过SMTP协议将邮件发送给邮件服务器，邮件服务器就会定时的向接收方发送链接请求
- 收件人在打算收信时，就运行PC机中的用户代理，使用POP3或IMAP协议读取发送给自己的邮件

# 安全通信

## 关注点
- 不可被窃取。只有接受者可以解密
- 不可伪造。消息确实来自发送者，而不是山寨的
- 不可被篡改。保证消息完整性

若使用对称加密实现，以上依赖于
- ***只有***发送者和接受者***两***者知道密钥

若使用非对称加密实现，以上依赖于
- 密钥对儿确实是对方的。接收者使用的发送者公钥*的确是*发送者的（而不是第三方山寨的），发送者的私钥没有泄漏；发送者使用的接收者公钥*的确是*接收者的，接收者的私钥没有泄漏

## 现有技术
- 加密和解密
  - 对称
  - 非对称
- 报文摘要（Message Digest）/消息验证码（Message Authentication Code，MAC）
- 数字签名
- SSL/TLS

以上各技术，分类上不是同级的，一些技术可能使用了其他技术。如数字签名可能用了非对称加密。

## See Also/外部资料
1. 《深入理解Java 7核心技术与最佳实践》ISBN 978-7-111-38039-9 Page 424 13.4加密与解密、报文摘要和数字签名
2. [Web of trust](https://en.wikipedia.org/wiki/Web_of_trust) at wikipedia.org
3. [Cryptography and Authentication via TLS with Web of Trust in Java](http://stackoverflow.com/questions/5721607/cryptography-and-authentication-via-tls-with-web-of-trust-in-java) at stackoverflow.com
4. [GnuTLS OpenPGP key support](http://www.gnutls.org/openpgp.html) at gnutls.org
5. [RFC 6091](https://tools.ietf.org/html/rfc6091)
6. [Comparison of TLS implementations](https://en.wikipedia.org/wiki/Comparison_of_TLS_implementations#cite_ref-openpgp_160-0) at wikipedia.org

1有较为系统的说明，虽然是针对Java 7平台的。

传统上/一般的TLS基于CA来保证公钥和所有者（如服务器）的所属关系（这个公钥确实是对方的），这种方式略为不灵活。2是另一种更为灵活的可达到类似功能的方式，OpenPGP、GPG等使用它。 3中讨论了让TLS使用它的办法。GunTLS是一个支持这种方式的C库，其相关说明在4。GunTLS实现了5，而且是目前（2015年12月16日）的唯一实现库，见6。

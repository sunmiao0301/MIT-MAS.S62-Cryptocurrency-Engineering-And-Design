## LECTURE 1: SIGNATURES, HASHING, HASH CHAINS, E-CASH, AND MOTIVATION

### 首先是第一步，这门课将与下面内容不相干

![image-20220811151109374](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202208111511657.png)

### 事物具有价值的原因：

- 稀有？
- 人们认为其有价值？
- 政府指定其作为交税的东西（对于传统货币而言）

### 传统银行的优缺点：

![image-20220811153042772](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202208111530038.png)

加密货币，需要解决的一个问题就是：怎么确保这枚货币没有被使用两次？（毕竟这枚货币只是一串数字，可以同时给到很多人）

### Hash function需要尽量满足的条件

- 不能被倒推出来，比如给你一个y，你将无法轻易得到那个hash(x) = y 的 x。（原像防御）
- 给定一个m1，你很难找到另一个m2，使得h(m1)=h(m2)。（弱碰撞防御）
- 就是你很难找到两个不同的m1和m2，使得h(m1)=h(m2)。（强碰撞防御）

如果符合强碰撞防御，也就是会符合弱碰撞防御，但是不一定符合原像防御。如果只满足前2个，在密码学上是不安全的，一般加密哈希函数应该满足1，2，3。

### 已经被破解的hash function（不要用）

- sha-1
- md5

### 关于加密

![image-20220811161224010](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202208111612129.png)

可以看到这张图，疑惑的是，为什么他要在自己加密的信息之后加一串“d79fe819”，原因就是防止被破译，比如你已经知道被加密的信息是关于什么的，并且知道hash结果，那么你可以通过大量的猜测并对比hash结果来反推，比如：

```bash
echo "I think it won't snow Wednesday !" | sha256sum
echo "I think it won't snow Monday !" | sha256sum
echo "I think it will snow Wednesday !" | sha256sum
echo "I think it won't rain Wednesday !" | sha256sum
```

那么很有可能就被你猜出来了。



### [签名](https://en.wikipedia.org/wiki/Lamport_signature) -- Lamport signature.

![image-20220811162227764](https://raw.githubusercontent.com/sunmiao0301/Public-Pic-Bed/main/imgfromPicGO/202208111622893.png)

GenerateKeys() --> 将生成公钥和私钥

Sign(secretKey, message) --> 通过私钥对要加密的信息进行签名，然后返回一个签名。

Verify(PublicKey, message, signature) --> 通过公钥验证签名。








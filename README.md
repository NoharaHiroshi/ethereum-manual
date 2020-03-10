# ethereum-manual
以太坊手册，记录所有和以太坊相关的问题及答案。

<br/>

## 一、基础知识相关

<br/>

### 1、以太坊发展有哪几个阶段，目前正处于什么阶段？

根据以太坊的发展路线，总共需要经历四个发展阶段，分别是：
  
1）**前沿（Frontier，2015年7月）**：以太坊网络第一次上线，开发者可以在上面挖以太币，开发dApp和各种工具。
  
2）**家园（Homestead，2016年3月）**：以太坊发布了第一个正式版本，对协议进行了优化。
  
3）**大都会（Metropolis，2017年10月）**：这个阶段分两次上线，分别是：  

* <strong>拜占庭（Byzantium，2017年10月）</strong> 加人了 EVM 指令，方便开发者编写智能合约。  
    
* <strong>君士坦丁堡（Constantinople，2019年1月）</strong> 引入 PoW 和 PoS 的混合模式，完成 PoW 向 PoS 的顺滑过渡。
  
4）**宁静（Serenity，时间待定）**：改用PoS共识，使用Casper共识算法。提高以太坊的交易速度、降低交易费用。
 
**目前阶段：大都会（君士坦丁堡）**

<br/>

### 2、以太坊区块奖励变化

1）前沿（Frontier，2015年7月）：**5ETH**

2）家园（Homestead，2016年3月）：**5ETH**

3）大都会（Metropolis，2017年10月）：**5ETH -> 3ETH -> 2ETH**

* 拜占庭是拜占庭（Byzantium，2017年10月）**5ETH -> 3ETH**
    
* 君士坦丁堡（Constantinople，2019年1月）**3ETH -> 2ETH**

<br/>

### 3、EIP是什么？ERC又是什么？有什么联系 ###

Ethereum Imporvement Proposals(以太坊改进建议)，简称EIP。是以太坊开发者社区提出的修改建议。

Ethereum Request For Comment (以太坊意见征求稿)，简称ERC，是以太坊上各种应用的开发标准和协议。

联系上讲，先有EIP，后有ERC。

开发者们先提出符合EIP要求的改进建议，经过不断讨论，细节与结论会放在ERC（Draft）中，最终被委员会批准，行成了ERC（Final）。

<br/>

### 4、ENS是什么？ ###

ENS（Ethereum Name Service）以太坊域名服务，类比DNS，是把域名解析为IP地址，而ENS是把.eth域名指向以太坊地址。

ETH域名可以让以太坊地址更容易记忆，转账交易时不用输入对方以太坊地址0x.......，只需要输入以太坊域名就可以完成交易。

<br/>

### 5、The Dao事件是什么？ ###

The Dao项目是区块链物联网公司Slock.it发起的一个众筹项目，参与人可以用手中的主流数字货币（BTC、ETH）去购买Dao币（The Dao发行的Token），持有Dao币的人可以参与投资议案的投票以及按照一定规则获得项目收益。

攻击者利用合约中的递归调用漏洞，将合约中的以太币非法转移到攻击者自己的账户中。

V神针对攻击，紧急提出了软分叉与硬分叉的解决办法。

The Dao事件导致ETH的价值从20美元跌落至13美元，并导致ETH分裂为ETC（经典以太坊，原链）和ETH（以太坊，新链）。

<br/>

### 6、ETH与ETC有什么区别与联系？ ###

2016年The Dao事件导致大量以太币被盗取，为了挽回损失，通过硬分叉回滚被盗的以太币，这样以太坊就分成两条链了。

一部分人认为即使发生攻击者盗取以太币事件，但完全去中心化，不应该因为蒙受损失就人为干预，这部分人支持旧链，仍在旧链上进行挖矿。这条旧链就是ETC（经典以太坊）。

一部分人支持回滚后的新链，这条新链继承了原来以太坊的名称，仍叫做ETH。

**ETH与ETC的区别**

1. ETC算力低，ETH算力高。

2. ETC使用POW共识机制，ETH在未来将会过渡至POS共识机制。

3. ETC在交易所的价值比ETH的低。

<br/>

### 7、软分叉与硬分叉？ ###

软分叉：软分叉的节点们都在同一条链上，旧的节点可以识别新节点挖出的区块，只是旧的节点无法完全理解新的区块。

硬分叉：硬分叉的节点们在不同的链上，旧的节点无法识别新节点发出的区块，不符合旧规则的区块将会被矿工拒绝接收。

软硬分叉，都可以向后兼容。

软分叉可以向前兼容，硬分叉不能向前兼容。

**软分叉与硬分叉的比较:**

1. 软分叉不会分散算力，硬分叉会分散算力。

2. 软分叉不要求所有节点同一时间升级，允许逐步升级。

3. 软分叉是对旧节点的欺骗，让旧节点无法感知区块已经发生了变化，违背了单点完整验证的原则。

4. 硬分叉后，持有者将会同时拥有新链与旧链的数字货币，对持有人有益。

5. 硬分叉可能会导致重放攻击。

<br/>

### 8、以太坊钱包是什么？ ###

以太坊钱包是用来存储和管理私钥的，并不存储ETH，ETH是存储在链上的。

以太坊钱包的主要功能是创建、保存、导出、恢复私钥。

<br/>

### 9、非确定性钱包与确定性钱包有什么区别？ ###

按照钱包内存储的私钥是否具备关联关系，分为非确定性钱包、确定性钱包。

* 非确定性钱包：钱包内存储的私钥都是由不同的随机数生成的，相互之间没有关联关系；迁移时，需要钱包内的所有私钥导出，在另一个钱包内导入。

* 确定性钱包：钱包内所有的秘钥都是由种子秘钥衍生出来的；迁移时，只需要把钱包内的种子秘钥导出，在另一个钱包内导入，其他私钥就可以再次由种子秘钥衍生。

<br/>

### 10、非确定性钱包的构成？ ###

非确定性钱包的私钥以JSON格式存储在keystore文件里。

    {
      "address": "001d3f1ef827552ae1114027bd3ecf1f086ba0f9",
      "crypto": {
        "cipher": "aes-128-ctr",
        "ciphertext": "233a9f4d236ed0c13394b504b6da5df02587c8bf1ad8946f6f2b58f055507ece",
        "cipherparams": {
          "iv": "d10c6ec5bae81b6cb9144de81037fa15"
        },
      "kdf": "scrypt",
      "kdfparams": {
        "dklen": 32,
        "n": 262144,
        "p": 1,
        "r": 8,
        "salt":
        "99d37a47c7c9429c66976f643f386a61b78b97f3246adca89abe4245d278840
      },
        "mac": "594c8df1c8ee0ded8255a50caf07e8c12061fd859f4b7c76ab704b17c957e842
      },
      "id": "4fcb2ba4-ccdb-424f-89d5-26cce304bf9c",
      "version": 3
    }

<br/>

### 11、助记词是什么？ ###

助记词是BIP-39的实现，用一组有序单词表示十六进制私钥，方便用户记忆。

生成过程：

1、钱包生成一个128bit或256bit的随机数，记为S。

2、用S的SHA-256哈希值的前几位（随机数位数/32）作为校验值，添加到随机数S的末尾，得到T。

3、将T按11bit为单位进行分组。

4、根据BIP-39的字典，得到每一组值对应的单词，保持原有次序，就获得了私钥的助记词。

随机数的位数与单词数量的关系

![pic_1](https://github.com/NoharaHiroshi/ethereum-manual/blob/master/img/img_1.png)

生成随机数并转化为助记词过程

![pic_2](https://github.com/NoharaHiroshi/ethereum-manual/blob/master/img/img_2.png)

<br/>

### 12、种子秘钥是什么？ ###

种子秘钥用于确定性钱包，确定性钱包可利用种子秘钥衍生出其他子秘钥。

助记词代表的128bit/256bit随机数，通过秘钥扩展算法（如PBKDF2），扩展为512bit长的数，这个数就是种子秘钥。

扩展算法需要2个参数：助记词和盐。

加盐的目的是在随机数的基础上，设置密码多一层保护。

生成过程：

1、PBKDF2秘钥扩展算法第一个参数是助记词。

2、PBKDF2秘钥扩展算法的第二个参数是盐.用户可以选择不设置盐，盐默认值为"mnemonic"，用户也可以选择设置盐，盐值为"mnemonic" + "用户设置值"。

3、PBKDF2秘钥扩展算法对助记词和盐进行2048轮哈希运算（HMAC-SHA512），产生一个512bit长的数。 这个数就是种子秘钥。

从助记词到种子秘钥的生成过程

![pic_3](https://github.com/NoharaHiroshi/ethereum-manual/blob/master/img/img_3.png)

由于种子秘钥是由助记词加上盐生成的，因此，即使助记词意外泄露，用户也无法获得种子秘钥。

<br/>

### 13、HD钱包是什么？ ###

HD钱包全称为分层确定性（Hierarchical Deterministic）钱包，钱包利用种子秘钥生成任意多的子秘钥，子秘钥生成任意多的孙秘钥，这些秘钥之间以树状层级结构相关联，因此叫做分层确定性钱包。

**主秘钥和主链码**

种子秘钥通过HMAC-SHA512哈希算法得到512bit数，其中左半部分（256bit）作为主私钥，右半部分（256bit）作为主链码，主私钥通过椭圆曲线算法推导出出主公钥，主公钥和主私钥组成主秘钥对。

**主秘钥生成子秘钥**

主秘钥生成子秘钥，通过子秘钥派生算法（Child Key Derivation Function，简称CKD），CKD生成子秘钥需要用到3个参数：

* 主秘钥（Parent Private/Public Key）

* 主秘钥链码（Parent Chain Code）

* 子秘钥序号（Child Index）

为了保证主秘钥生成子秘钥的过程不可逆，CKD使用单向哈希函数HMAC-SHA512，HD钱包中产生的任意子秘钥都可以作为新的主秘钥，衍生自己的子秘钥。

**主秘钥生成子秘钥过程**

1、 主公钥，主链码，子秘钥序号作为参数传给HMAC-SHA512哈希算法，得到512bit数T。

2、 把T拆成左右相等的256bit数L、R。

3、 L和主私钥通过CKD得到子私钥，L和主公钥通过CKD得到子公钥。

4、 R作为子节点链码。

主公钥生成子公钥

![pic_4](https://github.com/NoharaHiroshi/ethereum-manual/blob/master/img/img_4.png)

主私钥生成子私钥

![pic_5](https://github.com/NoharaHiroshi/ethereum-manual/blob/master/img/img_5.png)

<br/>

### 14、什么是扩展秘钥？ ###

扩展秘钥分为扩展公钥以及扩展私钥。

主公钥生成子公钥的时候，会用到主公钥、主链码。两者拼接后的数叫做扩展公钥（Extended Public Key），利用扩展公钥就可以创建子公钥了。

    Extended Public Key = Public Key + Chain Code     // 标记为 xpub，可用于派生子公钥
    
主私钥生成子私的时候，会用到主私钥、主链码。两者拼接后的数叫做扩展私钥（Extended Private Key），利用扩展私钥就可以创建子私钥与子公钥了。

    Extended Private Key = Private Key + Chain Code   // 标记为 xpriv，可用于派生子私钥和子公钥
   
由此可见，子公钥的生成不一定要用到子私钥，也可以由父公钥生成。

<br/>

### 15、什么是增强秘钥？ ###

增强秘钥是对扩展秘钥安全方面的补充。

考虑以下情况：

1、扩展公钥丢失：由于扩展公钥带有链码，那么就可以推导出所有的子公钥，即所有的子账户地址都会泄露。

2、扩展公钥丢失，子私钥丢失：通过扩展公钥、索引可以得到子秘钥的链码（子链码），子私钥可得到子公钥。子公钥结合子链码，则该子私钥下的所有孙子私钥都会被泄露。

可以看出，扩展公钥（公钥和链码）对钱包安全的重要性，那么如何进一步保证钱包的安全性呢？

BIP-32对CKD做出了改进，提出了增强子秘钥派生算法（Hardened Child Key Derivation，记为HCKD）。

CKD用主公钥与主链码生成子链码；HCKD用主私钥与主链码生成子链码。

HCKD中子私钥的生成不再依赖于主公钥，而是依赖于主私钥，因为私钥更容易受到用户重视，更不容易被泄露。缺点是不能再通过主公钥直接生成子公钥了，因为必须知道主私钥。

HCKD算法生成子秘钥

![pic_6](https://github.com/NoharaHiroshi/ethereum-manual/blob/master/img/img_6.jpg)

<br/>

### 16、什么是HD钱包秘钥路径？ ###

用于描述HD钱包中秘钥所在树形结构中的位置。

规定：

1、以M/m开头，表示公钥/私钥。

2、从左往右，以主密钥 -> 子秘钥 -> 孙秘钥的层级顺序排列。

3、每层秘钥之间以"/"隔开。

4、秘钥以在当层的索引表示，如m/0，表示主私钥衍生出的第一个子私钥，m/0'表示主私钥衍生出来的第一个增强子私钥。

举例：

* M/0/3/5：表示主公钥下第1个子公钥下的第4个孙公钥下的第6个重孙公钥。

* m/0'/1'/3'：表示主私钥下第1个增强子私钥下的第2个增强孙私钥下的第4个增强重孙私钥。

<br/>

### 17、HD钱包的树状结构导航？ ###

每个人HD钱包中秘钥的拓扑结构都是不同的，从一个HD钱包导入到另一个HD钱包时，如何恢复原有的树形拓扑结构呢？

BIP44提出了一个秘钥结构标准，种子秘钥可以在符合这个标准的钱包内导入导出，并恢复完整的秘钥拓扑。

BIP44定义了包含5个预定义树状层级的结构：

m / purpose' / coin_type' / account' / change / address_index

* purpose：符合BIP44标准的钱包，这个值固定为44'。

* coin_type：支持存储多种币的地址，例如BTC的值为0'，ETH的值为60'。

8 account：用户自定义用途，例如m/44'/0'/0'表示这是符合BIP44标准的比特币第一个主账户。m/44'/60'/1'表示这是符合BIP44标准的以太币第二个主账户。

* change：找零地址，这一层地址都是通过普通派生出来的私钥，目的是为了能在不安全的环境中展示。

* address_index：索引地址。

<br/>

### 18、冷钱包与热钱包？ ###

* 冷钱包：私钥隔离网络的钱包，也被叫做离线钱包。

* 热钱包：私钥接触网络的钱包。

<br/>

### 19、nonce是什么？在交易中起到什么作用？ ###

nonce值用来确定交易在链上的执行顺序，防止重复交易。

nonce值为用户发出的已被矿工确认的交易，例如nonce值为40，表示该账户已有序号从0到39共40笔交易被确认，新一笔交易的nonce值为40。

以太坊要求用户的每笔交易都有一个递增的nonce，用来表示交易发出的先后顺序，矿工也会按照nonce的顺序确认交易。nonce值小的表示先发生的交易，nonce值大的表示后发生的交易。这导致：

1、当提交多个交易时，其中一个交易发生问题，那么大于该笔交易nonce值的交易会被堵塞。除非发生问题的交易重新被确认，否则后面的交易将一直处于堵塞状态。

2、nonce值小于或等于已被确认交易的nonce值时，该笔交易会被节点拒绝。

<br/>

### 20、交易中有哪些参数？ ###

交易参数包括：

* nonce：用来确认交易执行的顺序。

* GasLimit：愿意为交易执行花费的最大gas。

* Price：每个gas的单价。

* Recipient：交易的接收方。

* Amount：转账数量。

* Payload：如果接收方是个人账户，则为备注。如果接收方是合约账户，则为要执行的函数，或创建合约。

* R、S、V：交易签名。

<br/>

### 21、交易签名中的R、S、V分别是什么？怎么得来的？ ###

R、V、S是由交易签名得来的。

签名Sig由以下方式得来，其中m为交易数据包、k为用户私钥。

    Sig = SigFunc(keccak256Func(m), k)
    
最后得到的签名Sig有65字节，将前64字节分为均等的2份，前32字节为R，后32字节为S，最后1字节为V。

R、S作为椭圆曲线计算参数，可以计算出两个可能的公钥，其中一个公钥是用户真实公钥。

V用来确定这2个公钥中的哪一个才是用户公钥。

<br/>

### 22、交易原始数据是否包含发送方字段？如果不包含，如何知道交易的发送方？ ### 

原始交易数据包是不包含发送方地址字段的，因为可以通过交易签名解析出发送方公钥，发送方公钥可以生成发送方地址。

交易中的签名部分，包含R、S、V三个部分。

通过R值在坐标轴上的x坐标，可以计算出椭圆曲线上的2点R、R1。椭圆曲线关于x轴对称，所有给定x值，在椭圆上有2个满足条件的点。这两个点对应用户可能存在的2个公钥，其中一个为用户真正的公钥。

为了方便获得用户公钥，交易签名中的V值就会告诉我们这个公钥中，哪一个是用户真正的公钥。

获得发送方的公钥后，就可以得到发送方的地址了。

<br/>

### 23、如何签名交易 ###

交易签名算法

    Sig = SigFunc(keccak256Func(m), k)
    
交易签名过程：

1. 首先先将原始交易进行RLP编码，得到m。

2. 再对m进行Keccak256哈希。

3. 最后将m的哈希值与私钥作为参数，进行椭圆ECSDA计算，得到签名。

交易签名算法的参数是交易数据包的Keccak256哈希值，而不是交易数据包本身。

最后将交易数据包与签名拼接起来，就得到了签名后的交易。

<br/>

### 24、如何检验签名 ###

校验签名过程：

1. 节点接收到交易，会先利用交易的签名部分（R、S、V）解析出发送方公钥，这个过程叫做公钥恢复。

2. 节点利用签名、公钥、以及交易数据的哈希值，计算出R\`值。

3. 用R\`和交易签名中的R进行比对，如果一致，则验证成功。

如果发生数据篡改，比如节点想要改动交易的数据，把Amount由1ETH改为10ETH，由于签名是通过用户私钥生成的，数据发生变化后，无法重新签名。其他节点接收到数据要进行校验，发现R\`与R对应不上，说明数据收到了篡改。

<br/>

## 二、ERC协议相关

<br/>

### 1、ERC20是什么？ ###

ERC20协议是基础数字货币协议，用于自建数字货币进行交易。

状态：**定稿（Final）**

符合ERC20协议的智能合约：

* 在创建时，会设置name、symbol、totalSupply、decimals属性来约定数字货币的名称、符号、发行量、最小可分割单位。

* 创建balanceOf来记录每个以太坊地址持有数字货币的情况。

* 提供transfer、transferFrom、approve、allowance方法来进行交易、委托交易。

* 直接兼容以太坊钱包。

<br/>

### 2、ERC233是什么？ ###

ERC223协议修复了ERC20的部分漏洞，防止ERC20 Token在交易过程中丢失。

状态：**草稿（Draft）**

ERC20的转账没有考虑到 <strong>“Token转到ERC20合约地址”</strong>这种情况的，一旦转给合约账户，这部分Token就无法被取出，也就相当于永远消失了。

ERC223在ERC20的基础上，新增判断接收方是否为智能合约：

* 接收方是个人账户，则使用原逻辑进行正常转账。

* 接收方是合约账户，则该合约需要实现tokenFallback来处理接收的Token，如果该合约没有实现tokenFallback方法，则Token不会进行转移。

**缺点**： 无法和现有ERC20 Token兼容，意味着原有的Token想从ERC20过渡到ERC223，需要重新部署。

<br/>

### 3、ERC721是什么？ ###

ERC721协议是非同质化数字货币协议。

状态：**定稿（Final）**

不同于ERC20 Token，ERC721中的每个Token都是独一无二的，每个Token均有不同的ID，不同ID有不同的解释。

CryptoKitties（谜恋猫）是第一个实现了ERC721 标准的去中心化应用。

ERC721 Token的最小可分割单位为1。

ERC721 标准合约必须实现ERC721接口、ERC165接口。

<br/>

### 4、ERC777是什么？ ###

ERC777协议对ERC20协议提出了诸多改进，可以视为ERC20的升级版本。

状态：**定稿（Final）**

ERC777试图对广泛使用的ERC20标准进行升级。包括：

* 支持默认操作员，默认可以代表所有持有者转移Token。这些操作员通常为交易所合约，或者自动扣费合约，持有者可以随时授权给操作员或撤销对操作员的授权。

* 采用与ETH同种逻辑转移Token，即使用send(dest, value, data)。

* 合约地址和个人地址都可以在ERC1820中注册一个包含tokensToSend或tokensReceived函数的合约来处理ERC777 Token交易通知，避免ERC20中存在的Token无法取出的问题。

* 交易新增data和operatorData字段，用来记录交易详情，类似于银行转账的备注。

* 可以向后兼容ERC20协议。

另外，需要注意：

* ERC777合约必须要通过ERC1820注册ERC777Token接口，以说明当前合约符合ERC777标准。如果ERC777要实现ERC20标准，还必须通过ERC1820注册ERC20Token接口

> 注册方法是： 调用 ERC1820 注册合约的 setInterfaceImplementer 方法，参数 _addr 及 _implementer 均是合约的地址，_interfaceHash 是 ERC777Token 的 keccak256 哈希值（0xac7fbab5...177054）

* granularity() 用来定义Token最小可切分单位（>=1），必须在创建时设定，之后不可以更改，不管是在铸币、发送还是销毁操作的Token数量，必需是粒度的整数倍。

* tokensToSend 钩子函数，必须在修改余额状态之前调用。

* tokensReceived 钩子函数，必须在修改余额状态之后调用。

<br/>

### 5、ERC1400是什么？ ###

ERC1400是部分可置换（Partially-Fungible）、证券型数字货币（STO）协议。用于实现证券相关业务功能。

状态： **草稿（Draft）**

ERC1400标准依赖于ERC1410标准。

ERC1400标准兼容ERC20、ERC777标准。

ERC1400标准将Token划分为不同分级（tranche），依据tranche对交易进行限制，如配股增发，投票表决，分红除息等复杂功能。

ERC1400标准实现证券业务会使用到证券增发（mint）、法律文件存储(setDocument)功能。

ERC1400标准实现强制转账功能，用于法律监管或资金回收。

ERC1400标准声明了canSend函数来实现转账限制，并利用canSend返回的状态码解释转账失败的原因。

<br/>

### 6、ERC1820是什么？ ###

ERC1820标准定义了一个通用接口注册表合约。

状态：**定稿（Final）**

合约账户和个人账户都可以在上面注册其实现的功能（个人账户通过代理合约实现）。

ERC1820依赖于一次性部署地址的无密钥部署方法部署合约，确保没有人控制注册表，从而确保信任。

ERC1820是一个全局合约，即使部署在不同的以太坊链上，它的地址总是

    0x1820a4B7618BdE71Dce8cdc73aAB6C95905faD24

ERC1820主要提供了2个接口：

    // @param _addr 合约地址或者个人地址
    // @param _interfaceHash 接口名称的keccak256
    // @param _implementer 实现合约
    setInterfaceImplementer(address _addr, bytes32 _interfaceHash, address _implementer) 
    
用来设置个人地址或合约地址（_addr）的接口（_interfaceHash）由哪个合约实现（_implementer）。

    // @param _addr 合约地址或者个人地址
    // @param _interfaceHash 接口名称的keccak256
    // @return 实现合约
    getInterfaceImplementer(address _addr, bytes32 _interfaceHash) external view returns (address)

用来查询个人地址或合约地址（_addr）的接口（_interfaceHash）由哪个合约实现（_implementer）。

存储结构：

    // 合约地址或者个人地址 => 接口名称的keccak256 => 实现合约
    mapping(address => mapping(bytes32 => address)) interfaces;

<br/>

### 7、ERC1404是什么？ ###

ERC1404是简单限制数字货币标准。是ERC20的扩展，在ERC20的基础上，增加了转移限制功能。

状态：**草稿（Draft）**

ERC1404目的在于限制ERC20 Token交易，以符合证券法规。

ERC1404在ERC20的基础上，新增了2个方法：

    // @notic 检查交易是否受限
    // @param from 发送方
    // @param to 接收方
    // @param value 转移token数量
    // @return uint8 状态码 0：成功
    function detectTransferRestriction (address from, address to, uint256 value) public view returns (uint8);

用于检查交易是否受限。受限内容包括：Token接收方是否通过KYC认证，是否在白名单中；发送方的Token是否在锁定期内被冻结等等。detectTransferRestriction返回非0值，则交易应该被回退。

    // @notic 查询交易受限原因
    // @param restrictionCode 状态码
    // @return string 交易受限原因
    function messageForTransferRestriction (uint8 restrictionCode) public view returns (string); 
    
用于检查交易受限的原因。

<br/>

### 8、ERC621是什么？ ###

ERC621是ERC20标准的扩展，增加了increaseSupply和decreaseSupply，用于增加发行量和减少流通量。

状态：**草稿（Draft）**

ERC621建议totalSupply应当是可修改的。

<br/>

### 9、ERC应用协议的兼容性？ ###

以ERC20为初始版本。

* ERC233向下兼容ERC20。

* ERC777向下兼容ERC20。

* ERC721不兼容ERC20。

* ERC1400向下兼容ERC20。

<br/>

## 三、合约设计相关

<br/>

### 1、如何判断address是个人地址还是合约地址？

    // 判断是否是个人地址
    function isRegularAddress(address _addr) internal view returns(bool) {
        require(_addr == address(0), "_addr is not allowed to be zero");
        uint size;
        // 内联汇编，通过获取地址的执行代码长度来判断是个人地址还是合约地址
        assembly { 
            size := extcodesize(_addr) 
        }
        return size == 0;
    }

<br/>

### 2、如何同时维护授权/撤销操作员记录，避免数据不一致？

补充：来源于ERC777中，合约需要同时记录持有人授权及撤销授权的操作员。并规定，在授权操作员记录中为True时，在撤销授权操作员记录中必须为False。

    contract A {
        // 默认操作员列表
        address[] internal defaultOperators;
        // 是否是默认操作员
        mapping(address => bool) internal isDefaultOperator;
        // 持有人授权的默认操作员
        mapping(address => mapping(address => bool)) internal authorizedOperators;
        // 持有人撤销的默认操作员
        mapping(address => mapping(address => bool)) internal revokedDefaultOperator;
        
        function authorizeOperator(address _operator) external {
            // 同时处理授权/撤销权限列表
            if (isDefaultOperator[_operator]) {
                revokedDefaultOperator[_operator][msg.sender] = false;
            } else {
                authorizedOperators[_operator][msg.sender] = true;
            }
            emit AuthorizedOperator(_operator, msg.sender);
        }
        
        event AuthorizedOperator(address indexed operator, address indexed tokenHolder);
    }


## 四、以太坊漏洞相关

<br/>

### 1、整数溢出漏洞

**类型**：合约漏洞。

**原理**：以太坊虚拟机（EVM）整数类型有固定的大小，意味着一个整型变量它的大小是有界限的。比如uint8类型的整型，它的取值范围\[0, 255\]，如果用uint8整形变量存储256时，这个整型变量的值将变成0。

    //BEC漏洞代码
    function batchTransfer(address[] _receivers, uint256 _value) public whenNotPaused returns (bool) {
        uint cnt = _receivers.length;
        uint256 amount = uint256(cnt) * _value;   // 漏洞点
        require(cnt > 0 && cnt <= 20);
        require(_value > 0 && balances[msg.sender] >= amount);

        balances[msg.sender] = balances[msg.sender].sub(amount);
        for (uint i = 0; i < cnt; i++) {
            balances[_receivers[i]] = balances[_receivers[i]].add(_value);
            Transfer(msg.sender, _receivers[i], _value);
        }
        return true;
      }

amount是由接受方数量与转账金额决定的，攻击者利用这两个值构建了一个超出uint256大小范围的值，例如2^256，此时amount值为0，绕过了balances\[msg.sender\] >= amount检查。最终，攻击者利用很小的代价为_receivers账户列表转入了大量的Token。

**检查及修复**：整数溢出的类型包括**乘法溢出，加法溢出，减法溢出**三种，检查所有涉及账户资产变动的方法，由其需要注意实际转账金额，是否是由用户输入金额经过计算得到的。建议使用OpenZeppelin的SafeMath 来处理算术逻辑，防止整数溢出漏洞。

<br/>

### 2、The Dao漏洞

**类型**：合约漏洞。

**原理**：**智能合约1**的**方法A**调用**智能合约2**中一个不存在的方法或者向**智能合约2**转账时，以太坊虚拟机（EVM）会将此次调用交给**智能合约2**中fallback方法处理。在fallback方法中再次调用**智能合约1**的**方法A**，就会形成递归，直至gas耗尽。

    The Dao漏洞代码（部分）
    // 智能合约1
    contract 1 {
        function splitDAO(uint _proposalID, address _newCurator) noEther onlyTokenholders returns (bool _success) {
            uint fundsToBeMoved = (balances[msg.sender] * p.splitData[0].splitBalance) / p.splitData[0].totalSupply;
            if (p.splitData[0].newDAO.createTokenProxy.value(fundsToBeMoved)(msg.sender) == false)
                throw;
            Transfer(msg.sender, 0, balances[msg.sender]);
            withdrawRewardFor(msg.sender);  // 1
            totalSupply -= balances[msg.sender]; 
            balances[msg.sender] = 0; 
            paidOut[msg.sender] = 0;
            return true;
        }

        function withdrawRewardFor(address _account) noEther internal returns(bool _success) {
            if ((balanceOf(_account) * rewardAccount.accumulatedInput()) / totalSupply < paidOut[_account])
                throw;
            uint reward = (balanceOf(_account) * rewardAccount.accumulatedInput()) / totalSupply - paidOut[_account];
            if (!rewardAccount.payOut(_account, reward)) // 2
                throw;
            paidOut[_account] += reward; 
            return true;
        }

        function payOut(address _recipient, uint _amount) returns (bool) {
            if (msg.sender != owner || msg.value > 0 || (payOwnerOnly && _recipient != owner))
                throw;
            if (_recipient.call.value(_amount)()) { // 3
                PayOut(_recipient, _amount);
                return true;
            } else {
                return false;
            }
        }
    }
    
    // 智能合约2(_recipient)
    contract 2 {
        function () {
          contract1.splitDAO(_proposalID, _newCurator); // 4
        }
    }

如标识的1->2->3->4，当合约1执行splitDAO方法时，由splitDAO -> withdrawRewardFor -> payOut顺序调用，payOut中的\_recipient.call.value(\_amount)()触发合约2的fallback函数，fallback函数又调用了合约1的splitDAO方法，形成了递归。

由于账户余额扣除与转账顺序有误（先进行转账，后进行余额扣除），攻击者在调用转账之后让方法进入了递归，导致扣除账户余额的操作被搁置。随着递归次数的增加，合约中的资产不断的被转移至攻击者的合约账户中。当满足递归结束条件，扣除了攻击者账户中的余额，方法执行结束。

**检查及修复**：
1. 采用正确的余额扣除和转账顺序（先进行余额扣除，再进行转账）。
2. 尽可能使用send方法进行转账（限制为2300gas），减少使用低阶方法call.value进行转账（会使用尽量多的gas）。

<br/>

### 3、重放漏洞

**类型**：链漏洞。

**原理**：以以太坊为例，The Dao事件后，ETH（原）硬分叉为ETC、ETH（新）。原来ETH（原）持有者，将会同时拥有硬分叉后的ETH（新）、ETC。由于ETH（新）与ETC交易数据格式、用户账户、用户私钥一致，因此在ETH（新）的交易信息，放到ETC上广播也能得到确认。利用这个漏洞，攻击者先向交易所充ETH（新），然后再提币，将提币的交易在ETC上进行广播，交易所就会将ETC打入到攻击者的ETC账户上。

**检查及修复**：
参照BTC与BCH的处理方法，BCH在签名时，在SIGHASH_TYPE上增加了一个FORK_ID位，并将自己的FORK_ID设置为0x40，BTC使用了区别于BCH的SIGHASH_TYPE，这样BCH交易的签名结果在BTC网络上验证不会通过，反之亦然，达到双向重放保护。

<br/>

### 4、call注入漏洞

**类型**：合约漏洞。

**原理**：call作为EVM的底层方法，可以对合约直接进行调用。

call两种调用方式:
    
    <address>.call(bytes);
    <address>.call(函数选择器，参数1，参数2...);
    
**攻击模式1：\<address\>.call(bytes)**
    
当智能合约中提供了一个方法，可以自定义调用方，及传入参数，那么这个合约就有可能存在call注入漏洞。
  
     contract A {
        function callCode(address _addr, bytes _data){
            _addr.call(_data);        
        }
        
        function transfer(address _to, uint256 _value){
          ...
        }
     }
     
调用合约的callCode方法，\_addr为contractA合约本身地址，\_data为调用trnasfer方法将合约账户Token转移给攻击者地址的bytes。执行方法后，合约账户中的Token就会转移到攻击者账户中。

**攻击模式2：\<address\>.call(函数选择器，参数1，参数2...)**
  
函数选择器为bytes4(keccak256("func(arg1,arg2)"))，如果合约中提供了一个方法，可以自定义调用方，函数选择器，参数，那么这个合约就有可能存在call注入漏洞。

    contract A {
        function callCode(address _addr, string _func, address _to, uint256 _value, bytes _data){
            _addr.call(bytes4(keccak256(_func)), _to, _value, _data);        
        }
        
        function transfer(address _to, uint256 _value){
          ...
        }
     }

用合约的callCode方法，\_addr为contractA合约本身地址，\_func为transfer(address,uint256)，\_to为攻击者账户地址，\_value为转移Token数量。执行方法后，call调用了当前合约的transfer方法，合约账户中的Token就会转移到攻击者账户中。

另外，由于EVM的call调用是根据ABI来解析参数的，callCode方法中的call调用transfer方法的时候，虽然传入了3个参数(\_to,\_value,\_data)，但EVM根据ABI(transfer(address,uint256))解析参数，发现该方法只需要两个参数，就会停止解析后面的内容(\_data)，因此调用在编译和运行阶段都是正常的。

**检查及修复**：

1. 尽量避免使用call调用。
2. 注意检查call调用是否可以自定义调用方，参数。
3. 对调用方及调用方法进行限制。

<br/>

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

ERC223协议是ERC20的补充协议，防止ERC20 Token在交易过程中丢失。

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

### 4、ERC1400是什么？ ###

ERC1400是部分可置换（Partially-Fungible）、证券型数字货币（STO）协议。用于实现证券相关业务功能。

状态： **草稿（Draft）**

ERC1400标准依赖于ERC1410标准。

ERC1400标准兼容ERC20、ERC777标准。

ERC1400标准将Token划分为不同分级（tranche），依据tranche对交易进行限制，如配股增发，投票表决，分红除息等复杂功能。

ERC1400标准实现证券业务会使用到证券增发（mint）、法律文件存储(setDocument)功能。

ERC1400标准实现强制转账功能，用于法律监管或资金回收。

ERC1400标准声明了canSend函数来实现转账限制，并利用canSend返回的状态码解释转账失败的原因。

<br/>


## 二、合约设计相关

<br/>

### 1、如何同时维护授权/撤销操作员记录，避免数据不一致？

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



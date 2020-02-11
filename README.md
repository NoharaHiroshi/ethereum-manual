# ethereum-manual
以太坊手册，记录所有和以太坊相关的问题及答案。

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


### 4、ERC20是什么？ ###

ERC20协议是基础数字货币协议，用于自建数字货币进行交易。

目前已**定稿（Final）**

符合ERC20协议的智能合约：

* 在创建时，会设置name、symbol、totalSupply、decimals属性来约定数字货币的名称、符号、发行量、最小可分割单位。

* 创建balanceOf来记录每个以太坊地址持有数字货币的情况。

* 提供transfer、transferFrom、approve、allowance方法来进行交易、委托交易。

* 直接兼容以太坊钱包。



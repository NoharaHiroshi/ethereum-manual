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

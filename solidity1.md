# 数据类型
## 整型
整数类型通过<kbd>int</kbd>和<kbd>uint</kbd>关键字定义，<kbd>int</kbd>代表有符号整数，<kbd>uint</kbd>代表无符号整数，对于<kbd>int</kbd>和<kbd>uint</kbd>可以显示设置占用空间大小，空间大小从8开始并且以8位步长递增，最大到256位，例如: <kbd>int8</kbd>、<kbd>uint8</kbd>、<kbd>uint16</kbd>等  
整型常量需要通过<kbd>constant</kbd>修饰符进行初始化，例如`int256 constant a=8`  
## 布尔型
布尔类型通过<kbd>bool</kbd>关键字定义，取值为<kbd>true</kbd>和<kbd>false</kbd>
## 地址类型
以太坊中的地址为160位，即20个字节大小，可以用<kbd>address</kbd>关键字定义  
### 地址类型的成员变量
可以使用<kbd>balance</kbd>属性来查询一个地址的余额，也可以使用<kbd>transfer</kbd>函数向一个地址发送以太币  
```javascript
address x = 0x123;
address myAddress = this;
if (x.balance < 10 && myAddress.balance >= 10) x.transfer(10);
```
## 字节数组
### 固定长度字节数组
固定长度字节数组是以<kbd>bytes</kbd>加上数字后缀的方式定义的，如<kbd>bytes2</kbd>表示两个字节长度的字节数组，数字后缀表示字节长度从1到32，以步长1递增
### 动态长度字节数组
动态长度字节数组分为两种：动态长度字节数组<kbd>bytes</kbd>和动态长度字符串<kbd>string</kbd>，<kbd>tstring</kbd>不提供长度和按索引访问方式  
## 数组
数组可以声明为定长数组，也可以是动态数组。固定长度类型的数组在声明时需要指定数组长度而且在后续使用过程中不能修改数组长度。动态数组在声明时不需要指定数组长度且在后续使用过程中可以动态添加元素
### 固定长度数组  
```javascript
uint[5] x=[1,2,3,4,5];
//修改
x[0]=6;
//获取数组长度
x.length;
```
### 动态数组
```javascript
bytes32[] names;
//添加元素
names.push("mike");
//修改
names[0]=bytes32("jetty");
//获取数组长度
names.length;
```
### 多维数组
在solidity语言中多维数组的行列位置和大多数编程语言是相反的，`uint[3][5] x`表示x是5行3列，多维数组可以声明为静态多维数组也可以声明为动态多维数组
## 字典
定义方式为<kbd>mapping(_KeyType => _KeyValue)</kbd>
```javascript
mapping (string => unit) public balances;
//设置
balances["charles"] = 1;
//返回值
balances["ada"];
//把元素设置为类型的初始值，整型会重置为0
delete balances;
```  
## 结构体
```javascript
struct Bank{
    address owner;
    uint balance;
}
//初始化
Bank c = Bank(msg.sender, 5);
//重新赋值
c.balance=15;
```
## 函数
### 函数定义
```
function 函数名(参数列表) returns (返回类型){
    ......
    return (返回值)
}
```
函数可以有多个返回值，当指明返回参数变量名字时，可以不需要显式返回  
```
function increment (uint x, uint y) returns (unit a, uint b){
    a = x + 1;
    b = y + 1;
}
```
### 函数的可见性
<kbd>public</kbd>：可以在合约内调用，通过交易调用，还可以被其他合约调用  
<kbd>private</kbd>：只能从定义它们的合约的内部访问  
<kbd>external</kbd>：可以被其他合约调用，也可以通过交易来调用  
<kbd>internal</kbd>：只能够从内部访问(当前合约内部或子合约内部)  
### 回退函数
每个合约中都有且仅有一个没有名字的函数，这个函数既无参数也无返回值  
一个没有定义回退函数的合约，如果接收ether，会触发异常，并返还ether，所以合约要接收ether，必须实现回退函数  
```
function () {
    ......
}
```
# 单位
## 时间单位
<kbd>seconds</kbd>、<kbd>minutes</kbd>、<kbd>days</kbd>、<kbd>weeks</kbd>、<kbd>years</kbd>均可作为后缀，默认以<kbd>seconds</kbd>为单位  
## 货币单位
可用后缀有<kbd>wei</kbd>、<kbd>finney</kbd>、<kbd>szabo</kbd>、<kbd>ether</kbd>，默认是<kbd>wei</kbd>  
# 全局变量
全局变量可以在合约脚本中任何地方使用，常用的有<kbd>this</kbd>、<kbd>msg</kbd>、<kbd>tx</kbd>、<kbd>block</kbd>
## this
<kbd>this</kbd>在合约中表示地址的引用  
<kbd>this.balance</kbd>：查询合约的余额
## msg
<kbd>msg</kbd>表示发送给合约的消息  
<kbd>msg.sender</kbd>：发送者的地址  
<kbd>msg.value</kbd>：发送给合约的以太币数量  
<kbd>msg.gas</kbd>：剩余gas  
## tx
<kbd>tx.origin</kbd>：交易发送者的地址  
<kbd>tx.gasprice</kbd>：交易的gas价格 
## block  
<kbd>block.number</kbd>：当前区块号  
<kbd>block.difficulty</kbd>：当前区块的难度  
<kbd>block.limit</kbd>：当前区块的gaslimit  
<kbd>block.coinbase</kbd>：当前区块矿工的地址  
<kbd>block.timestamp</kbd>：当前区块的时间戳  
# 继承
solidity合约中的继承通过<kbd>is</kbd>关键字实现，支持多重继承



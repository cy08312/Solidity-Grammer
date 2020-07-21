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
# 单位
## 时间单位
<kbd>seconds</kbd>、<kbd>minutes</kbd>、<kbd>days</kbd>、<kbd>weeks</kbd>、<kbd>years</kbd>均可作为后缀，默认以<kbd>seconds</kbd>为单位  
## 货币单位
可用后缀有<kbd>wei</kbd>、<kbd>finney</kbd>、<kbd>szabo</kbd>、<kbd>ether</kbd>，默认是<kbd>wei</kbd>


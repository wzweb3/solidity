# Solidity学习



材料：https://github.com/AmazingAng/WTF-Solidity.git



## Solidity 简介

`Solidity` 是一种用于编写以太坊虚拟机（`EVM`）智能合约的编程语言。我认为掌握 `Solidity` 是参与链上项目的必备技能：区块链项目大部分是开源的，如果你能读懂代码，就可以规避很多亏钱项目。

`Solidity` 具有两个特点：

1. "基于对象"：学会 `Solidity` 之后，可以助你在区块链领域找到好工作，挣钱找对象。
2. "高级"：不会 `Solidity`，在币圈会显得很 low。



## 开发工具

Remix

`Remix` 是以太坊官方推荐的智能合约集成开发环境（IDE），适合新手，可以在浏览器中快速开发和部署合约，无需在本地安装任何程序。

网址：[https://remix.ethereum.org](https://remix.ethereum.org)



## 值类型

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.4;

contract HelloWeb3 {
    string public _string = "Hello Web3!";
    // 布尔值
    bool public _bool = true;
    // 布尔运算
    bool public _bool1 = !_bool; // 取非
    bool public _bool2 = _bool && _bool1; // 与
    bool public _bool3 = _bool || _bool1; // 或
    bool public _bool4 = _bool == _bool1; // 相等
    bool public _bool5 = _bool != _bool1; // 不相等

    // 整型
    int256 public _int = -1; // 整数，包括负数
    uint256 public _uint = 1; // 正整数
    uint256 public _number = 20220330; // 256位正整数

    // 整数运算
    uint256 public _number1 = _number + 1; // +，-，*，/
    uint256 public _number2 = 2**2; // 指数
    uint256 public _number3 = 7 % 2; // 取余数
    bool public _numberbool = _number2 > _number3; // 比大小

    // 地址
    address public _address = 0x7A58c0Be72BE218B41C608b7Fe7C5bB630736C71;
    address payable public _address1 = payable(_address); // payable address，可以转账、查余额
    // 地址类型的成员
    uint256 public balance = _address1.balance; // balance of address

    // 固定长度的字节数组
    bytes32 public _byte32 = "MiniSolidity";
    bytes1 public _byte = _byte32[0];

    // 用enum将uint 0， 1， 2表示为Buy, Hold, Sell
    enum ActionSet {
        Buy,
        Hold,
        Sell
    }
    // 创建enum变量 action
    ActionSet public action = ActionSet.Hold;

    // enum可以和uint显式的转换
    function enumToUint() external view returns (uint256) {
        return uint256(action);
    }
}

```



## 函数

 Solidity 中函数的形式:

```solidity
function <function name>(<parameter types>) {internal|external|public|private} [pure|view|payable] [returns (<return types>)]
```


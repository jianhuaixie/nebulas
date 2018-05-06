# Nebulas 底层技术之Nelulas虚拟机

### NVM - Nebulas Virtual Machine
在Nebulas中，NVM是一个非常重要的概念。正如所描述的名称一样，它为智能合同和协议代码提供了托管虚拟机执行环境。

[go-nebulas](https://github.com/nebulasio/go-nebulas "go-nebulas") 现在提供两种虚拟机：

- V8:Chrome V8
- LLVM:Low-Level Virtual Machine

### Nebulas V8 Engine

在go-Nebulas中，我们设计并实现了基于Chrome V8引擎的Nebulas V8引擎。

Nebulas V8引擎为智能合同执行提供了高性能的沙盒。它保证用户部署的代码在托管环境中运行，并防止主机上大量的资源消耗。由于使用了Chrome V8，JavaScript和TypeScript是用于Nebulas智能合同的一流语言。任何熟悉JavaScript或TypeScript的人都可以编写自己的智能合同，并在Nebulas V8中运行。

下面是一个用JavaScript编写的智能合约例子：

	"use strict";

	var BankVaultContract = function(){
		LocalContractStorage.defineMapProperty(this,"bankVault");
	};

	// save value to contract,only after height of block,users can takeout
	BankVaultContract.prototype = {
		init:function() {},
		save:function(height){
			var deposit = this.bankVault.get(Blockchain.transaction.from);
			var value = new BigNumber(Blockchain.transaction.value);
			if (deposit != null && deposit.balance.length>0){
				var balance = new BigNumber(deposit.balance);
				value = value.plus(balance);
			}
			var content = {
				balance.value.toString(),
				height:Blockchain.block.height + height
			};
			this.bankVault.put(Blockchain.transaction.from,content);
		},
		
		takeout:function(amount){
			var deposit = this.bankVault.get(Blockchain.transaction.from);
			if (deposit==null){
				return 0;				
			}
			if (Blockchain.block.height < deposit.height) {
	            return 0;
	        }
			var balance = new BigNumber(deposit.balance);
	        var value = new BigNumber(amount);
	        if (balance.lessThan(value)) {
	            return 0;
	        }
	        var result = Blockchain.transfer(Blockchain.transaction.from, value);
	        if (result > 0) {
	            deposit.balance = balance.dividedBy(value).toString();
	            this.bankVault.put(Blockchain.transaction.from, deposit);
	        }
	        return result;
		}
	};
	module.exports = BankVaultContract;


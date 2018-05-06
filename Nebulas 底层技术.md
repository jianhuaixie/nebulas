# Nebulas 底层技术之智能合约

### 智能合约

使用的语言是JavaScript和TypeScript。基本选用JavaScript就好。

这两种语言都能被google的Chrome V8引擎所支持。

只能合约在Nebulas中跟用面相对象的语言所编写的类很相似。这些类有变量和方法，方法能修改这些变量，变量所代表的数据能持久化保存。

##### 编写智能合约

一个智能合约必须包含一个init方法，这个方法只会在合同部署的时候被执行。以_开头的方法是private的，在事务处理过程中不能被执行。其他的方法为public，在事务处理过程中是可执行的。

由于智能合约是在Chrome V8中执行的，所以所有的实例变量都在内存中，所以将所有的实例保存在Nebulas的state trie中是不明智的。在Nebulas中，我们提供LocalContractStorage和GlobalContractStorage对象来帮助开发人员定义需要保存到state trie的字段。这些字段应该在合同的构造函数中定义，在其他函数之前。

比如下面是一个简单的智能合约例子：


	class Rectangle {
		constructor(){
			// define fields stored to state trie
			LocalContractStorage.defineProperties(this,{
				height:null,
				width:null,
			});
		}
		
		//init function
		init(height,width) {
			this.height = height;
			this.width = width;
		}

		// calculate area function
		calculateArea(){
			return this.height*this.width;
		}
		
		// verify function
		verify(expected){
			let area = this.calculateArea();
			if(expected != area){
				throw new Error("Error:expected "+ expected + " ,actual is "+ area + ".");
			}
		}
	}

### 可见性

在Nebulas中，定义两种可见性，public和private。在JavaScript中，不需讨论函数可见性问题，所有方法定义在原型对象中都是public。

- public   public方法能够在事务处理中被调用
- private  以_开头，只能被public方法调用

### LocalContractStrorage

LocalContractStrorage模块提供一个基于存储容量的state trie。其只能接受字符串的key value对。所有数据都存储在与当前智能合约地址相关的私有state trie中，只有当前智能合约可以访问它们。

### BigNumber

BigNumber模块利用的是bignumber.js脚本，一个用于任意精度的十进制和非十进制算法的JavaScript库。智能合约可以直接使用BigNumber来处理交易的值和其他值的转移。

	var value = new BigNumber(0);
	value.plus(1)
	...

### Blockchain

Blockchain模块为智能合约提供了一个对象，用于获取当前合约执行的交易和区块。此外，NAS可以从合约中转移，并提供地址检查。

	//current block
	Blockchain.block;
	
	//current transaction,transaction's value/gasPrice/gasLimit auto change to BigNumber object
	Blockchain.transaction;

	// transfer NAS from contract to address
	Blockchain.transfer(address,value);

	// verify address
	Blockchain.verifyAddress(address);

下面是一个用上面模块的例子：

	'use strict';
	var SampleContract = function(){
		LocalContractStorage.defineProperties(this,{
			name:null,
			count:null
		});
		LocalContractStorage.defineMapProperty(this,"allocation");
	};

	SampleContract.prototype = {
		init:function(name,count,allocation){
			this.name = name;
			this.count = count;
			allocation.forEach(function(item){
				this.allocation.put(item.name,item.count);
			},this);
			console.log('init: Blockchain.block.coinbase = ' + Blockchain.block.coinbase);
	        console.log('init: Blockchain.block.hash = ' + Blockchain.block.hash);
	        console.log('init: Blockchain.block.height = ' + Blockchain.block.height);
	        console.log('init: Blockchain.transaction.from = ' + Blockchain.transaction.from);
	        console.log('init: Blockchain.transaction.to = ' + Blockchain.transaction.to);
	        console.log('init: Blockchain.transaction.value = ' + Blockchain.transaction.value);
	        console.log('init: Blockchain.transaction.nonce = ' + Blockchain.transaction.nonce);
	        console.log('init: Blockchain.transaction.hash = ' + Blockchain.transaction.hash);
		},

		transfer:function(address,value){
			var result = Blockchain.transfer(address,value);
			console.log("transfer result:",result);
			Event.Trigger("transfer",{
				Transfer:{
					from:Blockchain.transaction.to,
					to:address,
					value:value
				}
			});
		},

		verifyAddress: function (address) {
	    	var result = Blockchain.verifyAddress(address);
	        console.log("verifyAddress result:", result);
	    }
	};
	module.exports = SampleContract;


### Event

Event模块记录智能合约中的执行事件。记录的事件存储在链上的event trie中，它可以用FetchEvents方法（execution transaction hash 作为参数）在区块中以来获取。所有的智能合约事件主题都有一个chain.contract. 前缀，在他们订立智能合约的主题之前。
	
	Event.Trigger(topic,obj);

- topic : user-defined topic
- obj  : JSON object


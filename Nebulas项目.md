# Nebulas项目

## 最烂系列榜单，电影
> 基本功能：添加数据,查询列表并排名，评分

接口：

- save(movie_name,describe,date) 参数：电影名字，describe为描述信息，date为添加时间，返回：电影的详细信息，功能：添加电影信息
- get(movie_name)	参数:电影名字，返回：电影的详细信息，功能：取电影的详细信息
- getTop10()	参数：无，返回：排序后的top10的烂电影，功能：取最烂的10部电影
- like(movie_name)	参数：电影名字，返回：电影的详细信息，功能：点赞
- notlike(movie_name)	参数：电影名字，返回：电影的详细信息，功能：点踩
- len()	参数：无，返回：已添加的电影数量，功能：查看已添加数据
- forEach(limit,offset)	参数：limit取多少条数据，offset为起始点，返回：电影列表，功能：遍历查询数据

## 最烂系列榜单，歌曲

> 基本功能：添加数据，查询数据，分页查询，评分

接口：

- save(song_name,singer,describe,date) 参数：song_name歌曲名字，singer为歌手名字，describe为描述信息，date为添加时间，返回：歌曲的详细信息，功能：添加歌曲信息
- get(song_name)	参数:歌曲名字，返回：歌曲的详细信息，功能：取歌曲的详细信息
- getTop10()	参数：无，返回：排序后的top10的烂歌曲，功能：取最烂的10部歌曲
- like(song_name)	参数：歌曲名字，返回：歌曲的详细信息，功能：点赞
- notlike(song_name)	参数：歌曲名字，返回：歌曲的详细信息，功能：点踩
- len()	参数：无，返回：已添加的歌曲数量，功能：查看已添加数据
- forEach(limit,offset)	参数：limit取多少条数据，offset为起始点，返回：歌曲列表，功能：遍历查询数据

## 全球最具影响力的100人评选

> 基本功能：添加数据，查询数据，分页查询，评分

接口：

- save(famous_name,profession,portrait,describe,date) 参数：famous_name名人名字，profession为名人所在行业，portrait为名人头像url，describe为描述信息，date为添加时间，返回：名人的详细信息，功能：添加名人信息
- get(famous_name)	参数:名人名字，返回：名人的详细信息，功能：取名人的详细信息
- getTop10()	参数：无，返回：排序后的top100的影响力名人，功能：取最具有影响力的100位名人
- like(famous_name)	参数：名人名字，返回：名人的详细信息，功能：点赞
- notlike(famous_name)	参数：名人名字，返回：名人的详细信息，功能：点踩
- len()	参数：无，返回：已添加的名人数量，功能：查看已添加数据
- forEach(limit,offset)	参数：limit取多少条数据，offset为起始点，返回：名人列表，功能：遍历查询数据

## 全球最有可能的10个黑天鹅事件

> 基本功能：添加数据，查询数据，分页查询，评分

接口：

- save(event_name,profession,describe,date) 参数：event_name事件名字，profession为事件所在行业，describe为描述信息，date为添加时间，返回：事件的详细信息，功能：添加事件信息
- get(event_name)	参数:事件名字，返回：事件的详细信息，功能：取事件的详细信息
- getTop10()	参数：无，返回：排序后的top10的黑天鹅事件，功能：取最具有黑天鹅性质的10个事件
- like(event_name)	参数：事件名字，返回：事件的详细信息，功能：点赞
- notlike(event_name)	参数：事件名字，返回：事件的详细信息，功能：点踩
- len()	参数：无，返回：已添加的事件数量，功能：查看已添加数据
- forEach(limit,offset)	参数：limit取多少条数据，offset为起始点，返回：事件列表，功能：遍历查询数据 

## 最具创新精神企业榜单

> 基本功能：添加企业信息支付费用，评论企业支付费用，点赞支付费用，点踩支付费用，查询列表并排名

- save(enterprise_name,profession,portrait,describe,date) 参数：enterprise_name企业名字，profession为企业所在行业，portrait为企业logo图的url,describe为描述信息,此处需要组拼成这样："[{\"comment\":\"超级棒\",\"date\":\"201805071459\"}]"，date为添加时间，返回：企业的详细信息，功能：添加企业信息
- get(enterprise_name)	参数:企业名字，返回：企业的详细信息，功能：取企业的详细信息
- getRanking()	参数：无，返回：排序后的具有创新精神的企业，功能：取具有创新精神的企业排名列表
- comment(enterprise_name,describe) 参数：enterprise_name企业名字，describe为评论，需要组拼成这样的格式："[{\"comment\":\"很牛的一家公司\",\"date\":\"201805071459\"}]" ,返回：评论列表。功能：为该企业添加评论
- like(enterprise_name)	参数：企业名字，返回：企业的详细信息，功能：点赞
- notlike(enterprise_name)	参数：企业名字，返回：企业的详细信息，功能：点踩
- len()	参数：无，返回：已添加的企业数量，功能：查看已添加数据
- forEach(limit,offset)	参数：limit取多少条数据，offset为起始点，返回：企业列表，功能：遍历查询数据 


## 最具创新精神企业家榜单

> 基本功能：添加企业家信息支付费用，评论支付费用，点赞支付费用，点踩支付费用，查询列表并排名

## 赌注合约（先知机）

> 基本功能：添加赌注，手续费设置，先知机代码公开，自动决断，转移Token

接口：

- searchFinishBet(date) 参数:date为追溯到的时间，返回：已经完结的赌约列表，功能：查询已经完结的赌约
- showBeingBet()	参数：无，返回：未完结的赌约，功能：返回未完结赌约列表
- gamble(bet_name,which_bet_party,value)	参数：bet_name表示对哪份赌约进行下注，which_bet_party表示对赌注的哪一方下注，value表示下注币数量，返回：true/false	功能：下注
- isClosing(bet_name)	参数：bet_name为赌约名字，返回：true/false 功能：判断这个赌约是否已经完结需要进行结算
- balance(bet_name)	参数：bet_name为赌约名字，返回：结算成功true/失败false	功能：对某个赌约进行结算
- transfrom(from,to,value)	参数：from为支出地址，to为汇入地址，value为币数量	功能：吊起合约外部的支付接口进行支付

### 火星地皮，西班牙女王-哥伦布基金

> 基本功能：划分火星地皮到最小单位，地图选择一块地皮，设置地皮价格，购买地皮，转手地皮，基金使用用途登记（资金转移地址，资金大小，资金用途），发起基金使用投票

## 星星所有权售卖，结合装饰品

> 星星添加支付费用，星星列表可供选择，购买上链宣誓主权支付费用，登记客户信息，收取费用并制作星星装饰品发货给客户

## 机器人地图数据自动售卖

> 将物联网节点的导航应用地图进行售卖，挂单，匹配订单，交易订单，允许使用数据

## 表白墙 ExpressLoveWall

> 添加表白对象，查看表白对象

- save(express_name,expresser,love_story,date)
	- 参数：表白对象名字，表白者名字，爱情故事，日期
	- 返回：添加成功信息/False

## 财产公开信息

> 自愿登记财产信息

## 智能保险柜

> n个用户对一笔资金进行管理，需要m(m<=n)个用户签名同意才能对一笔资金进行转移

## 产生利息的币额宝

> 用户可以将币按照一定的利息存放到币额宝，利息是通过有些用户借币需求而来，需要登记借币者个人信息，并通过审核，然后借币者提交借币订单，智能合约让放币者自动匹配和借币者的订单。如果违约，平台方不负责任，只会把借币者信息给到放币者。

## 慈善基金组织募捐地址审核等级平台

> 智能合约众多项目需要将收入捐给慈善基金，而现有的很多慈善基金都还没开通数字币募捐地址，这个平台就是要打造这样一个平台，对慈善机构进行严格核查，给币圈一个可信的慈善基金清单。

## 族谱记录

> 族谱信息非常重要，历来都是集中式保存，也容易出现损坏威胁，如果将族谱信息记录到区块链，能永久保存下去，是不是很妙。



### 星云提交DAPP地址

- jianhuaixie@gmail.com 
	- 项目一：Top10 Sucks Movies
		- 合约地址：n1qLyPZhDPj267uW7JLNdV6F8M7eMYrTBXy
		- 合约hash：84b8c9e6ce7c9420293b5b6f54c1e15978b09ed8cd2c126fd0bcc038f87ef7ff
- 125532273@qq.com
	- 项目二：Top10 Sucks Song
		- 合约地址：n1x33QSRTDs3yQetaHVpYxKbzcePVcz72oE
		- 合约hash：05a913124d1352becc18bc3b196b542b259415064b971da38f6d39f81df71a23
- xiejianhuai@wiair.com
	- 项目三：Top100 Influential Famous
		- 合约地址:n1k3JZdycUGkJ7BdKFU3hSjwnhuQG2qMP7r
		- 合约hash：0e0e48fca27bf4bdd2b76619dd9fe23e8258ab1c7c8c4d37b6fa03e69f40efd1
- chenxiaomeng@wiair.com
	- 项目四：Top10 Black Swan Event
		- 合约地址：n1r7Lkr6kkrcadt16gYYD2czNtudefVJaF9
		- 合约hash：54a52409c521df0d0a993fbb3846970e179dbb9d6c96449f5f10c4e0efa645c0

- wuzhiliang@wiair.com
	- 项目五：Innovating Enterprise Ranking
		- 合约地址：n1qCqFxPmxTh6cYeEHuVmWFXyDC7e5NzoQx
		- 合约hash：42670c845dbcc6f098cb7cbf178734e80265b01934c7025dfdf00659592ecc8d

- silverxie7@163.com	walletAddress:n1HvEJCLSKG32VoxEbNZhFss5oaRqNx1HGU
	- 项目六：Express Love Wall


- silverxie7@126.com	walletAddress:n1JsTBsnYtXerDsRrFA9mFJtmVD5wsiT6XT
	- 项目七：

- nebulasking@163.com	walletAddress:n1H8voJW6PLCdnfYth9HYGPkMNeD1gtav9w
	- 项目八：

- maskfollws@sina.com	walletAddress:n1btDnA5DVmiLF7mDnoGiCUuX9UFF4txxg1
	- 项目九：

- maskfollows@sina.com	walletAddress: n1c1T1ydt3FAfRi8zAZ5WVNunssdJ77hQu6
	- 项目十：

- trumpisawesome@sina.com	walletAddress:n1aysWWg3A6zDWZSS7b2njR8RQHYSvUeYK4
	- 项目十一：

- romeisrome@sina.com	walletAddress:n1Zb5AduAg8wHi8h8PQMUooKNmExVdCqD4v
	- 项目十二：

- nebulasisawesome@sina.com	walletAddress:n1Q8sSUG6VTASjw3NneaDf3viqcgwX9HVCD
	- 项目十三

- nebulasissogood@sina.com	walletAddress:n1TMzSfqUgHah9ngygUX8ghtDS2xPBzWn5H
	- 项目十四

- ilovenebulas@sina.com	walletAddress:n1bfwxzxchubdhnmtdNtUgh5jGwLuravLt8
	- 项目十五

- ilovenebulas@sina.com	walletAddress:n1GpiemXcHx3GfXusWvDzZMMi7Jsbw2ongz
	- 项目十六

- blockchainking@sina.com	walletAddress:n1ZkusWARiQAaYq7Q8CUi9yrkUdsskf4476
	- 项目十七

- smartcontract@sina.com	walletAddress:n1SuzPP1DXzVp6JR1SfanLc2hAGa7fGYXyy
	- 项目十八

- blockchaintec@sina.com	walletAddress:n1PMnNQG7bBuDJJzysMEfsyciuZc1RjHLM5
	- 项目十九

- hashgraph@sina.com	walletAddress:n1V8aTV8JeDLzcWoBrZRcyhcY3geBJhguGg
	- 项目二十

- dagtec@sina.com	walletAddress:n1MPTR82zhgm62itxdgHnbXAW7bAK4YPhaa
	- 项目二十一








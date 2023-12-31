
# NFT
铸造3中不同类型的NFT
1. 基本NFT(openZeppelin)
2. IPFS NFT(hosted on IPFS)
- 利用随机性生成独特的NFT
3. SVG NFT(hosted on chain)
- 信息保存在链上

## 使用方法
部署
```bash
yarn hardhat deploy
```
测试
```bash
yarn hardhat test
```
测试覆盖率
```bash
yarn hardhat coverage
```
## 部署到测试网
### 1. 环境变量

您需要设置以下两个环境变量，并将它们添加到 .env 文件中

`SEPOLIA_RPC_URL`

`PRIVATE_KEY`

- `SEPOLIA_RPC_URL`：您正在使用的Sepolia测试网节点的url，您可以从Alchemy网站 https://www.alchemy.com/ 免费获得
- `PRIVATE_KEY`：您账户的私钥（如metamask）。请使用不含任何真实资金的私钥
### 2. 获取测试网ETH
前往 https://faucets.chain.link/ 获取一些测试网 ETH 和 LINK。
### 3. 设置Chainlink VRF
前往https://vrf.chain.link/ 注册一个新的订阅并向该订阅添加LINK，获取一个 subscriptionId，将该subscriptionId添加到`helper-hardhat-config.js`。如果您已经拥有旧订阅，则可以重复使用旧订阅。
运行
```bash
yarn hardhat deploy --network sepolia --tags main 
```
只部署 --tags main, 因为我们需要添加RandomIpfsNFT合约地址作为VRF的消费者
### 4. 添加合约地址作为Chainlink VRF的消费者
返回https://vrf.chain.link/ 并在您的订阅下添加Add consumer并添加您的合约地址。
### 5. 铸造NFT
运行
```bash
yarn hardhat deploy --network sepolia --tags mint
```









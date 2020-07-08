## Contract design patterns
### 1. Contract destruction ![contract-destruction](https://i.imgur.com/DT2hfD0.jpg)
- Sending tracsaction to dead contract: fail
- ALL fund send to dead contract will be lost
### 2. Factory contract
### 3. Name registry pattern
Using a registry Contract to manage all contracts, then using contract name to access instance of a particular contract
### 4. Mapping iterator pattern
- Use another array to keep keys ![mapping-itorator-pattern](https://i.imgur.com/FZPwB1Tg.jpg)
- Storage cost goes up
- Cost of iteration goes up
### 5. Withdrawal pattern
- Send vs transfer ![send-vs-transfer](https://i.imgur.com/wzaCgxO.jpg)
- Withdrawal pattern ![withdrawal-pattern](https://i.imgur.com/0lYuucS.jpg)
![](https://i.imgur.com/m5wyFD1.jpg)

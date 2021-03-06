### 交易手续费及找零 \| Transaction Fees And Change

交易的手续费是基于交易的体积计算的。每字节的手续费是根据当前开采区块对空间的需求计算的，费用随着需求增加而增加。何在去快链部分解释的一样，交易费支付给打包出区块的矿工，最终每个矿工选择接受他们将接受的最低交易费。

还有一个概念是 “high priority transactions”，高优先级交易，指的是包含那些很久未交易的比特币的交易。

过去这些交易都是免费的，在Bitcoin Core 0.12 之前，每个块的50KB用来优先打包这些交易。但是现在默认情况下这个值为0K，在优先区域打包满之后，所有交易根据他们的每字节费用进行排序，先打包交易费高的交易，直到所有可用空间已经填满。

从比特币0.9开始，一笔交易需要的最低费用（目前是1000 聪）会被网络广播，任何只支付最低费用的交易会等待很长时间，直到有一个块有足够空间来打包它。请参阅付款验证部分来了解最低交易费的重要性。

因为每个交易花掉了Unspent Transaction Outputs 未花费输出集合\(UTXOs\)中的比特币，并且应为UTXO只能被花费一次，每次交易UTXO 的一部分会给矿工作为交易费。很少有人想要支付的金额和自己的UTXO 是匹配的，所以大部分的交易会有一个用来找零的ouptut。

找零output和其他output 一样，只是将交易剩余的比特币返还给支付者。他们可以使用和在input是在UTXO中相同的P2PKH 公钥哈希和P2SH 脚本哈希，但是出于下一节要阐述的原因，强烈不建议这样做。


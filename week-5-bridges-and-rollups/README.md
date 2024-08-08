# Week 5: Bridges and Rollups

## Bridges

This week we'll cover some basics in bridges and rollups. We believe the world will be cross-chain and Harmony is investing heavily in being at the center of this new world. To achieve this, we need some way of communicating between L1 and L2 blockchains and this can be achieved efficiently with bridges. However, just as different blockchains have different stances on the [scalability trilema](https://vitalik.eth.limo/general/2021/04/07/sharding.html), different bridges have different stances on the [interoperability trilemma](https://blog.connext.network/the-interoperability-trilemma-657c2cf69f17). With zero knowledge we can take bridges even further. We can have bridges with focus on the privacy of the users. Some good examples are Webb and Aztec. 

{% embed url="https://youtu.be/8Te5TkcYi54" %}

{% embed url="https://youtu.be/YyAaZb5ALCM" %}

## Rollups

By now you've certainly heard about rollups. These are systems that achieve smaller transaction fees due to the batching of transactions. Instead of every user submitting their own transaction, they transact onto the rollup and the rollup batches these transactions together and submits them on-chain after specified periods of time (or number of transactions). Read [this](https://ethereum.org/en/developers/docs/scaling/) for a deeper understanding.

The ones in production are mainly optimistic rollups. These have the downside of the long lock-times that are required by the fraud proof scheme they use. With zero-knowledge we can eliminate the need for fraud proofs as all transaction batching would have a proof, so there would be no way of actually cheating the rollup. You should also read [this](https://ethereum.org/en/developers/docs/scaling/zk-rollups/).

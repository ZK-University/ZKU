# W5 Assignment

## Section A: Theoretical Questions
### Part 1: Scalability

The scalability trilemma is a well known problem in the blockchain space. Ethereum has decided to focus on providing decentralization and security, while leaving scalability to layer-2 solutions. These rollup applications (optimistic or zk) are usually referred to as scaling solutions and they can be built for other blockchains as well.

1. Choose two specific  blockchain scaling solutions and compare their implementations regarding the different trade-offs they make.
2. [ZkSync](https://zksync.io/) and [StarkNet](https://starkware.co/starknet/) are two of the most promising zkRollups currently available with differing strategies. Briefly explain the differentiations between the two rollups and your conclusion on which is more likely to win the zkRollup wars.

NB: Most of these questions have no exact correct answer and grades will be awarded based on your depth of understanding of the question and ability to properly back your points.

### Part 2: Interoperability

One can say this is the future of blockchain, as it opens up the users to a wide variety of options and flexibilities. Couple inter-chain communications with zk-privacy, then the sky's the limit.

1. Briefly explain what would be the different components required to create a bridge application for token transfers. Assume ERC20 tokens are being transferred between EVM chains for simplicity.
2. Aztec utilizes a set of zero-knowledge proofs to shield both native assets and assets that conform with certain standards (e.g. ERC20) on a Turing-complete general-purpose computation.​​ Briefly explain the concept of AZTEC Note and how the notes are used to privately represent various assets on a blockchain.

### Part 3. Final Project

Deciding on a final project requires research on similar projects. **Post a final project proposal** in a discord channel cohort-5. You should present a description of your final project and compare it to **at least two** similar applications in development / production. You should mention what are the advantages and disadvantages of your project over the similar ones you studied. **Design the circuits (if applicable) for your project idea, and provide the code for it in the assignment submission.**

## [Optional] Section B: Coding Questions

### [Optional] Part 4. Rollups

For this assignment we'll see what would be some of the circuits needed to construct a zero-knowledge rollup. For this assignment, you will build the circuits under 1_verify_eddsa, 2_verify_merkle and 3_single_tx [in this repo](https://github.com/zku-cohort-4/week5). Instructions are included in the README and in code comments.
Note that single_tx builds on top of the verification of the eddsa signature. Merkle-tree implemented in `2_verify_merkle` is different from the one you already implemented. This circuit checks if there is a valid merkle-proof for a leaf in any of the valid merkle-roots. These different merkle-roots can represent merkle-trees in different chains for example.

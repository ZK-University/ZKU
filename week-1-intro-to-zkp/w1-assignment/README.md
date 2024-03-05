# W1 Assignment

**Week 1 repo:** https://github.com/zku-cohort-4/week1

> [!NOTE]
> Fork the above repo onto your own Github and **run** `git submodule update --init --recursive` to **pull all submodules**. Group your coding assignment submission into a single commit. Link the commit to the submission text box. All word answers should go into a single PDF file to be uploaded here.

## Part 1 Theoretical background of [zk-SNARKs and zk-STARKS](https://consensys.net/blog/blockchain-explained/zero-knowledge-proofs-starks-vs-snarks/)

1. Explain in 2-4 sentences why SNARK requires a trusted setup while STARK doesn’t.
2. Name two more differences between SNARK and STARK proofs.


## Part 2 Getting started with circom and snarkjs

Circom is perhaps the single most important tool we will be using throughout this course. Let’s get familiar with it!

1. Follow the instructions on [Circom 2 Documentation](https://docs.circom.io/getting-started/installation/) to install circom (2.0.3 or above) and snarkjs@latest on your machine (Windows users are recommended to install via WSL). Read through the rest of the documentation to learn about the syntax of the circom language. You might also find this [tutorial](https://github.com/enricobottazzi/ZKverse) and this [tutorial](https://www.samsclass.info/141/proj/C523.htm) useful.

2. Fork the `Week 1` repo and go into the Q2 directory. Install all the node dependencies. In the `contracts/circuits` folder, you will find `HelloWorld.circom`. Run the bash script `scripts/compile-HelloWorld.sh` to compile the circuit. Answer the following questions (word answers should go into the PDF file):

    1. What does the circuit in `HelloWorld.circom` do?

    2. Lines 7-12 of `compile-HelloWorld.sh` download a file called `powersOfTau28_hez_final_10.ptau` for Phase 1 trusted setup. Read more about how this is generated [here](https://blog.hermez.io/hermez-zero-knowledge-proofs/), [here](https://blog.hermez.io/hermez-trusted-setup-phase-2/), and [here](https://blog.hermez.io/hermez-cryptographic-setup/). What is a Powers of Tau ceremony? Explain why this is important in the setup of zk-SNARK applications.

    3. Line 24 of `compile-HelloWorld.sh` makes a random entropy contribution as a Phase 2 trusted setup. How are Phase 1 and Phase 2 trusted setup ceremonies different from each other?`

3. In this question, you will learn about an important restriction on circom circuits:

    1. In the empty `scripts/compile-Multiplier3-groth16.sh`, create a script to compile `contracts/circuits/Multiplier3.circom` and create a verifier contract modeling after `compile-HelloWorld.sh`.

    2. Try to run `compile-Multiplier3-groth16.sh`. You should encounter an `error[T3001]` with the circuit as is. Explain what the error means and how it arises.

    3. Modify `Multiplier3.circom` to perform a multiplication of three input signals under the restrictions of circom.

4. In the empty `scripts/compile-Multiplier3-plonk.sh`, create a script to compile `circuit/Multiplier3.circom` using PLONK in snarkjs. Add a `_plonk` suffix to the build folder and the output contract to distinguish the two sets of output.

    1. You will encounter an error `zkey file is not groth16` if you just change `snarkjs groth16 setup` to `snarkjs plonk setup`. Resolve this error and answer the following question - How is the process of compiling with PLONK different from compiling with Groth16? 

    2. What are the practical differences between Groth16 and PLONK? Hint: compare and contrast the resulted contracts and running time of unit tests (see Q5 below) from the two protocols.

5. So far we have not tested our circuit yet. While you can verify your circuit in the terminal using `snarkjs groth16 fullprove`, you can also do so directly in a Node.js script. We will practice doing so by creating some unit tests to try out our verifier contract(s):

    1. Running `npx hardhat test` will prompt an error `HH606`. Before we can test our verifier contracts with hardhat, we must modify the solidity version. In `scripts/bump-solidity.js`, we have already written the regular expressions to modify `HelloWorldVerifier.sol`. Add script to `bump-solidity.js` to do the same for your new contract for `Multiplier3`.

    2. You can now perform the unit tests for `HelloWorldVerifier` by running `npm run test`. Add inline comments to explain what each line in `test/test.js` is doing.

    3. In `test/test.js`, add the unit tests for `Multiplier3` for both the Groth16 and PLONK versions. Include a screenshot of all the tests (for `HelloWorld, Multiplier3 with Groth16`, and `Multiplier3 with PLONK`) passing in your PDF file.


## Part 3 Reading and designing circuits with circom

Though it will be nice if we write entirely innovative circuits for every project we create, we should also utilize existing circuit libraries to help us. In this question, you will be learning about two such libraries that you can import to create more complicated circuits. To start, go into the `Q3` directory in `Week 1` repo and run `npm install` in each project folder to install the dependencies.

1. [circomlib](https://github.com/iden3/circomlib) is the official library of circuit templates released by iden3, the creator of Circom. One important template included is `comparators.circom`, which implements value comparisons between two numbers. The following questions will cover the use of this template in our own circuits:

    1. `contracts/circuits/LessThan10.circom` implements a circuit that verifies an input is less than 10 using the `LessThan` template. Study how the template is used in this circuit. What does the 32 in Line 9 stand for?

    2. What are the possible outputs for the `LessThan` template and what do they mean respectively? (If you cannot figure this out by reading the code alone, feel free to compile the circuit and test with different input values.)

    3. Proving a number is within a range without revealing the actual number could be useful in applications like proving our income when applying for a credit card. In `contracts/circuits/RangeProof.circom`, create a template (not circuit, so don’t add `component main = ...`) that uses `GreaterEqThan` and `LessEqThan` to perform a range proof.

2. [circomlib-matrix](https://github.com/socathie/circomlib-matrix) is a library covering basic matrix operations, modeled after circomlib, and created by our very own mentor Cathie. Matrix operations can be useful in puzzles (e.g. [zkPuzzles](https://github.com/zku-cohort-3/zkPuzzles), [zkGames](https://github.com/vplasencia/zkGames)), image processing (e.g [zkPhoto](https://github.com/socathie/zkPhoto)), and machine learning (e.g. [zk-mnist](https://github.com/0xZKML/zk-mnist), [zk-ml](https://github.com/zk-ml/demo)). Let’s take a look at matrix operations in action in a [Sudoku](https://en.wikipedia.org/wiki/Sudoku) circuit in the [zkPuzzles](https://github.com/zku-cohort-3/zkPuzzles) repo.

    1. In `projects/zkPuzzles/circuits`, modify Lines 20-23 of `sudoku.circom` so that it implements the check on the inputs to be between 0 and 9 (inclusive) using your `RangeProof` template from 1.3.

    2. You can run `npm run test:fullProof` while inside the `zkPuzzles` directory to test your modified circuit. You are expected to encounter an error. Record the error, resolve it by modifying `project/zkPuzzles/scripts/compile-circuits.sh`, and explain why it has occurred and what you did to solve the error.

    3. Copy your modified `sudoku.circom` into `contracts/circuits/sudokuModified.circom` for submission, so you don’t have to commit the submodule.

3. *[bonus]* Matrix operations could also be used to verify that someone knows a solution to [a system of (linear) equations](https://en.wikipedia.org/wiki/System_of_linear_equations) without revealing the solution itself. In `bonus/SystemOfEquations.circom`, implement a general circuit that verifies an input `x` solves the system of equations `Ax=b`, where `A` and `b` are also signal inputs. Then run `npm run test` to prove that the solution to the following system of equations is `x=15, y=17, z=19`.\
`x + y + z = 51`\
`x + 2y + 3z = 106`\
`2x - y + z = 32`

4. *[bonus]* Apart from the standard `circomlib` library and `circomlib-matrix` library that performs matrix operations, what other libraries do you think could be created to help foster the growth of ZK applications?

Further resources:
- [Circom Unit Testing](https://learn.0xparc.org/materials/learning-group-1/circom-unit-testing/)


# W3F Maintainance Grant Proposal

- **Project Name:** Solang Maintenance

- **Contributor Name:** Salaheldin Soliman

- **Payment Details:** USDT (ERC20)

- **Address**: 0xf19d225a4b7dc1fcc53fbdad5a3d87bce53af3c6

- **[Level](https://github.com/w3f/Grants-Program/tree/master#level_slider-levels):** 1


## Project Overview :page_facing_up:

### Overview

Solang compiles Solidity smart contracts to Substrate and Solana targets. An in-depth overview of Solang's purpose and motivation can be found at https://hyperledger.github.io/hyperledger-hip/HIPs/solang.html.


### Maintenance Project Details

The aim of this maintenance project is to improve the Solidity developer experience on Substrate chains through undertaking the following two milestones:

- [lmprove debug buffer usage](https://github.com/hyperledger/solang/milestone/5):

  - The debug buffer can be used by the smart contract as a way to comminucate with the developer during runtime, e.g. for printing messages or displaying the return code of API calls into the runtime environment. Currently, the debug buffer lacks any kind of structure, which can make for an awkward debugging experience. The goal is to use a JSON data structure within the debug buffer. This makes its usage more human friendly and even allows front-end tools to parse the content of the debug buffer in a defined way.

  - Currently, runtime errors are lost. Solang inserts an `unreachable` instruction, causing nothing more than a regular `trap` in case of runtime errors (like arithmetic overflows, failed assert statements, etc..). The aim here is to output the runtime error in the formatted debug buffer, so that a developer knows what went wrong (this doesn't even happen in Ethereum's solc currently). The line number of the solidity source file in which that error is encountered will be displayed as a further improvement.

  - The debug buffer is not something meant to be used in production deployments (pallet contracts does not even support this in production setups). However, at the time of writing, `solang` does not have any means to omit all code generation related to the debug buffer. This results in (potentially a lot of) wasted gas. So another goal of this milestone is to implement a CLI flag for the compiler that effectively turns all logic related to debug printing into No-Op.
  

- [Solang projects](https://github.com/hyperledger/solang/milestone/6):

  - At the time of writing, the only way to configure the compilers behaviour is to use CLI flags and options. An ever-growing list of compiler options (like optimization flags) and possible runtime configuration options is making this more and more awkward. This information can be provided to the compiler via a `TOML` file, similar to what we see in other languages (e.g. `Cargo.toml`).

  - To make this work, the compiler will need to implement functionality to parse its options out of such a `TOML` file. Additionally, some tooling should be implemented to help our users working with it. The first one will be a new sub-command `solang new`, which generates a new "Project" containing `Solang.toml` file with sensible defaults as well as some Solidity flipper example contract. Naturally, the `new` subcommand provides some configuration options itself, like specify the project name or runtime target.

  - A further issue addressed here is that a soldity developer using Solang currently has no way to tell the compiler some information like contract authors and version. Since this information is needed for metadata generation, it is just populated with some non-meaningful default value. As a consequence, at the time of writing, `solang` users need to edit the metadata file manually after each and every compilation.

  - Another improvement is for specifying the runtime target configuration. As-is, developers only have some low-level options like specifying the `address` and `balance` (`value`) size used by the runtime size themselves. A better solution would be able to provide high-level representations of currently deployed on-chain runtime configurations and the compiler will take care of the rest. For instance, providing a target configuration of "Substrate version `X`" or "pallet contract nodes version `Y`" will inform the compiler to generate contracts compatible with the default configuration of pallet contracts in substrate version `X` or contacts node version `Y` respectively. Other possilbe options for the user should be to just directly specify the parachain, e.g. `Rococo` or `Shiden` (randomly named examples).
 

### Ecosystem Fit
 

**Who is your target audience and how does your project fit into the ecosystem?**

We still have along way to go in terms of developer experience with Solidity on Substrate based chains. Although Solang as a compiler itself can be considered a huge step towards attracting solidity developers to the Polkadot/Kusama ecosystems: The Solidity developer experience on Ethereum far exceeds that of "Solidity Contracts on Substrate", caused by our inferior tooling and debugging story. The mentioned improvements are some immediate measures to address that. This grant will benefit any substrate parachain looking to leverage the possibility of using Solidity for their own good, as it will help level the developer experience for Solidity developers regardless whether they target Ethereum or Substrate.
  

## Contributor :busts_in_silhouette:

### Contact


- **Contact Name:** Salaheldin Soliman

- **Contact Email:** salaheldin_sameh@aucegypt.edu

  
### Relevant Experience

  

Worked on Solang as part of the [Hyperledger Mentorship Program](https://wiki.hyperledger.org/display/INTERN).
1. Implemented [array bounds checks optimization](https://solang.readthedocs.io/en/latest/code_gen_options.html#array-bound-checks-optimization).
2. Implemented [multiplication overflow detection during runtime](https://github.com/hyperledger/solang/pull/988).
3. Implemented [constant overflow detection during compilation](https://github.com/hyperledger/solang/pull/1024#ref-commit-baaa425).
4. Improved [Solang's parser resilience](https://github.com/hyperledger/solang/pull/1068).

  

### Github Handle

 
- https://github.com/salaheldinsoliman

  

### LinkedIn Profile

  
- https://www.linkedin.com/in/salaheldinsoliman/

 

## Development Roadmap :nut_and_bolt:
  

### Overview of the Features/Bugs That Need Development Contributions:

#### Milestone 1: Improve debug buffer usage
- [Use structured data in the debug buffer](https://github.com/hyperledger/solang/issues/1048) 
- [Print execution errors in the debug buffer](https://github.com/hyperledger/solang/issues/1083)
- [Execution errors to be passed with source file and line number](https://github.com/hyperledger/solang/issues/972)
- [Bug: Substrate Integration tests fail to compile with -g](https://github.com/hyperledger/solang/issues/1051)
Time Estimate: 4 months
FTE (Full time Equivalent): 0.5

#### Milestone 2: Implement [Solang projects](https://github.com/hyperledger/solang/milestone/6):
Time Estimate: 2 months
FTE (Full time Equivalent): 0.5


  

### Assurance That the Current Project Owners Are Willing to Review/Accept Your Contributions:

Discussions with project owner [Sean Young](sean@mess.org) and maintainer [Cyrill Leutwiler](cyrill@parity.io) resulted in that the issues presented above would be reviewed and merged.

 

### Overview / Budget

  
- **Start Date:** December 20, 2022

- **Estimated Duration:** 6 Months

- **Sprint/Period Duration:** 
    First period(milestone):  4 months
    Second period(milestone): 2 months

- **Full-Time Equivalent (FTE):** 0.5 FTE (20h per week)

- **Budget per period:** 
    First period(milestone):  $3,000
    Second period(milestone): $2,000
  
- **Total Costs:** $5,000



## Current and Future Plans

- Improve Substrate developer experience via the above-mentioned tasks
- Continue improving Solang till maturation from the Substrate side.
- Possibly develop an IDE based on Solang that matches Ethereum's Remix

  

## Additional Information :heavy_plus_sign:

 
**How did you hear about the Grants Program?**

Recommendation from Solang's maintainers [Sean Young](sean@mess.org) and [Cyrill Leutwiler](cyrill@parity.io) 

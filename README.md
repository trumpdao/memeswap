# Fork of Terraswap for using (xy)^2 = k

In finance and economics, the equation xy = k is often used to represent the concept of a constant product or liquidity in a market. This equation states that the product of the quantities of two assets, denoted as x and y, remains constant during a trade. As a result, if the quantity of one asset increases, the quantity of the other asset must decrease proportionally to maintain the constant product.

However, in some scenarios, it may be desirable to introduce a non-linear relationship between the quantities of the two assets. This is where the equation (xy)^2 = k comes into play. By squaring the product of the quantities, we create a non-linear relationship that emphasizes a preference for not selling.

Here's an explanation of why we might choose to use (xy)^2 = k:

Encouraging long-term holding: The squared relationship promotes the idea of long-term holding of assets. When (xy)^2 = k, the value of xy must remain constant, but the squared term amplifies any changes in x or y. Consequently, this encourages participants to hold onto their assets rather than constantly trading or selling them.

Reducing volatility: The non-linear relationship helps dampen market volatility. Minor fluctuations in one asset's quantity will have a less pronounced effect on the other asset's quantity due to the squaring operation. This characteristic can be beneficial in stabilizing markets and avoiding excessive speculation.

Emphasizing stability and sustainability: By favoring not selling and promoting long-term holding, the (xy)^2 = k equation aligns with a mindset focused on stability and sustainability. It encourages market participants to consider the long-term value and potential of their assets rather than engaging in short-term trading strategies.

It's important to note that the decision to use (xy)^2 = k instead of xy = k depends on the specific context and goals of the market or system being considered. While the squared relationship offers certain advantages, it may not be suitable for all situations and may introduce its own complexities. Therefore, careful consideration and analysis are required when choosing the appropriate equation to model a particular market or system.

# TerraSwap
[![terraswap on crates.io](https://img.shields.io/crates/v/terraswap.svg)](https://crates.io/crates/terraswap)
[![workflow](https://github.com/terraswap/terraswap/actions/workflows/tests.yml/badge.svg)](https://github.com/terraswap/terraswap/actions/workflows/tests.yml)
[![codecov](https://codecov.io/gh/terraswap/terraswap/branch/main/graph/badge.svg?token=ERMFLEY6Y7)](https://codecov.io/gh/terraswap/terraswap)

Uniswap-inspired automated market-maker (AMM) protocol powered by Smart Contracts on the [Terra](https://terra.money) blockchain.

## Contracts

| Name                                               | Description                                  |
| -------------------------------------------------- | -------------------------------------------- |
| [`terraswap_factory`](contracts/terraswap_factory) |                                              |
| [`terraswap_pair`](contracts/terraswap_pair)       |                                              |
| [`terraswap_router`](contracts/terraswap_router)   |                                              |
| [`terraswap_token`](contracts/terraswap_token)     | CW20 (ERC20 equivalent) token implementation |

* terraswap_factory

   Mainnet: `terra1466nf3zuxpya8q9emxukd7vftaf6h4psr0a07srl5zw74zh84yjqxl5qul`

   Testnet: `terra1jha5avc92uerwp9qzx3flvwnyxs3zax2rrm6jkcedy2qvzwd2k7qk7yxcl`

* terraswap_pair

   Mainnet (CodeID): 5

   Testnet (CodeID): 84

* terraswap_token

   Mainnet (CodeID): 4

   Testnet (CodeID): 83

* terraswap_router

   Mainnet: `terra13ehuhysn5mqjeaheeuew2gjs785f6k7jm8vfsqg3jhtpkwppcmzqcu7chk`

   Testnet: `terra1xp6xe6uwqrspumrkazdg90876ns4h78yw03vfxghhcy03yexcrcsdaqvc8`

## Running this contract

You will need Rust 1.44.1+ with wasm32-unknown-unknown target installed.

You can run unit tests on this on each contracts directory via :

```
cargo unit-test
cargo integration-test
```

Once you are happy with the content, you can compile it to wasm on each contracts directory via:

```
RUSTFLAGS='-C link-arg=-s' cargo wasm
cp ../../target/wasm32-unknown-unknown/release/cw1_subkeys.wasm .
ls -l cw1_subkeys.wasm
sha256sum cw1_subkeys.wasm
```

Or for a production-ready (compressed) build, run the following from the repository root:

```
docker run --rm -v "$(pwd)":/code \
  --mount type=volume,source="$(basename "$(pwd)")_cache",target=/code/target \
  --mount type=volume,source=registry_cache,target=/usr/local/cargo/registry \
  cosmwasm/workspace-optimizer:0.12.6
```

The optimized contracts are generated in the artifacts/ directory.

# 🚰 Tranches, Liquidity Pool, Vaults and Reserve

{% hint style="info" %}
This page contains formulas written in LaTex. For the best reading experience, please view this page on Desktop.
{% endhint %}

### Terminology Recap:

**Junior Tranche Investors =>** Institutional/High-Net Worth Individuals/Corporate/DAO Treasury Investors. Undergo a decentralised KYC/B process.

**Liquidity Pool Investors =>** Retail investors _and_ Junior Tranche Investors who invest in the Liquidity Pool, which funds the Senior Tranche of trades. Anyone with a Solana wallet can participate as a Liquidity Pool Investor.

**Trade =>** The process of trading future recurring revenue (tokenised and securitised into an NFT asset-backed security) between a business and investors.

**Vault =>** Where the trade takes place. The NFT asset-backed security is locked into a vault to act as collateral to trade against.

**Liquidity Pool =>** Where Liquidity Pool Investors stake their USDC.

### Overview&#x20;

Current TradFi platforms similar to Revflow's model utilise Venture Debt or Institutional investor capital as their source of liquidity. For example, platforms that utilise Venture Debt borrow the debt at x% and sell it on to businesses at x+2% or more, retaining the spread as revenue on the deal. Likewise, with institutional investor capital, platforms utilise just-in-time financing where the institutional investor keeps the capital on their books and funds deals as and when they come in, with the platform taking a percentage fee for facilitating the transaction.

Revflow is building upon the latter. Junior Tranche Investors fund trades with just-in-time financing, whilst Liquidity Pool Investors will deposit capital into the Liquidity Pool, which funds the Senior Tranche of trades on a continuous basis with excess liquidity being siphoned through the Reserve. This section will go over the mechanics behind Tranches, the Liquidity Pool and Vaults for Trades, alongside the Reserve mechanism.

![Revflow Liquidity Mechanism. Please click on the image to view in high-resolution.](<../../.gitbook/assets/Liquidity Flow (1).png>)

## Tranches&#x20;

Monthly subscription revenues for a business are bundled together and tokenized into an NFT Asset-Backed Security which is deposited into a Vault and used as collateral to trade against. Current TradFi platforms that securitise recurring revenue into tradable assets have the following drawbacks:

* Only institutional/corporate investors can participate in these trades, locking retail out of potential yield&#x20;
* Institutional/corporate investors have to bare the risk of the entire trade (they cannot partially fund a deal)&#x20;

Tranches allow investors to spread the risk, whilst opening the market up for retail investors to generate yield off these products via DeFi. Trades consist of two tranches:&#x20;

1. **Junior Tranche**
2. **Senior Tranche**&#x20;

To make sense of the Junior and Senior Tranche Yield calculations, we must first understand the basics of the **Trade Value** , the **Asset Value** and the **Trade Yield.** The Trade Value is the amount of capital the business requests to receive from the Revflow platform and is also the amount that investors invest into the Junior and Senior Tranches to fund the trade. The **Asset Value** is the amount of future recurring revenue that is required as collateral and will be paid back to the Vault on a monthly basis:&#x20;

$$
Asset\:Value\:=\:\frac{Trade\:Value}{(1\:-\:Discount\:Rate)}
$$

For example, if a business requests $1,000,000 in upfront capital (the **Trade Value**) and they have a 9.5% Discount Rate, the **Asset Value** will be:

$1,000,000 / (1 - 0.095) = **$1,104,972**

| Asset Value | Discount Rate | Trade Value |
| ----------- | ------------- | ----------- |
| $1,104,972  | 9.5%          | $1,000,000  |

For now, the Maturity Term will be static at 12 months, so repayments are calculated as:&#x20;

$$
Monthly\:Repayments\:=\:\frac{Asset\:Value}{12}
$$

Therefore monthly repayments into the Vault for an **Asset Value** of $1,104,972 are:

$1,104,972.38 / 12 = **$92,081**

The **Trade Yield** is the overall yield between the Trade Value and the Asset Value, which is not the same as the Discount Rate (due to the value increasing vs. being discounted). To calculate the Trade Yield, we use the following formula:

$$
Trade\:Yield\:=\:\frac{Asset\:Value}{Trade\:Value}\:-1
$$

Therefore, the **Trade Yield** for the example above is:&#x20;

($1,104,972.38 / $1,000,000.00) - 1 = **10.4972% APY**

Thus, the inverse of the table above becomes:&#x20;

| Trade Value | Trade Yield  | Asset Value |
| ----------- | ------------ | ----------- |
| $1,000,000  | 10.4972% APY | $1,104,972  |

Again, the **Trade Yield** is the overall yield that the Vault will accrue; the difference between the Trade Value and the Asset Value. However, it is not the Yield % that the Junior or Senior Tranches will obtain due to differing levels of risks and Revflow fees involved. The section below goes over the mechanics for the Junior and Senior Tranche calculations.

### Junior Tranche&#x20;

The Junior Tranche takes the higher risk on each trade by performing the underwriting (first-loss capital), and thus receive higher returns in comparison to the Senior Tranche due to the **Junior Fee** (a premium for underwriting the trade). Additionally, rather than funding an entire trade like similar TradFi platforms, Junior Tranche Investors only need to fund a portion of the deal. For example, a leverage ratio for 4:1 would imply that Junior Tranche investors fund 20% of the trade whilst the Senior Tranche funds the remaining 80%. Unlike the Senior Tranche, the Junior Tranche funds trades via just-in-time financing. Junior Tranche investors receive a Junior Token, which represents their stake in the Junior Tranche of a specific trade.

Yield is accrued on a monthly basis alongside the monthly portion of the principal. Junior Token holders can redeem the principal and yield each month as the USDC repayments flow into the Vault, which they can then withdraw to their wallet, fund new trades or siphon the repayments into the Liquidity Pool. Please view the [Examples](example.md) page to see a breakdown of Junior Tranche returns with monetary values.

The following calculations are utilised to identify the Junior Yield %:

**Full Junior Yield % APY:**

_This does not include the Revflow Junior Yield, which is the fee for facilitating the transaction._

$$
Full\:Junior\:Yield\:=\:Trade\:Yield\:*(1\:+\:Leverage\:Ratio\:*\:Junior\:Fee)
$$

**Revflow Junior Yield % APY:**

_The amount Revflow takes to facilitate the transaction._

$$
Revflow\:Junior\:Yield\:=\:Full\:Junior\:Yield\:*\:Revflow\:Junior\:Fee
$$

**Junior Yield % APY:**

_The amount the Junior Tranche yields after the Revflow yield fee. This is the yield value Junior Tranche investors will receive._

$$
Junior\:Yield\:=\:Full\:Junior\:Yield\:-\:Revflow\:Junior\:Yield
$$

### Senior Tranche&#x20;

The Senior Tranche of trades takes a lower risk as the Liquidity Pool acts as a continuous stream of capital to fund each trade. In turn, the Liquidity Pool is effectively an index on the Senior Tranches of trades, alongside any additional yield gained from the Reserve. Anyone can participate in the Liquidity Pool, thus anyone can participate in the Senior Tranche of trades, which is protected by first-loss capital. Liquidity pool participants are given an LP Token when they deposit USDC into the LP. This token represents the participants stake in the pool, and as yield and repayments flow back into the LP (alongside reserve yield), the net asset value of the LP Token increases.&#x20;

Yield is accrued on a monthly basis alongside the monthly portion of the principal. LP Token holders do not need to redeem from individual Vaults; instead, the repayments are automatically sent back to the Liquidity Pool where they are then re-invested into the Senior Tranche of new trades or invested via the Reserve.  Please view the [Examples](example.md) page to see a breakdown of Senior Tranche returns with monetary values (_for individual trades_).&#x20;

The following calculations are utilised to identify the Senior Yield %:

**Full Senior Yield % APY:**

_This does not include the Revflow Senior Yield; which is the fee for facilitating the transaction._

$$
Full\:Senior\:Yield\:=\:Trade\:Yield\:*(1\:-\:Junior\:Fee)
$$

**Revflow Senior Yield % APY:**

_The amount Revflow takes to facilitate the transaction._

$$
Revflow\:Senior\:Yield\:=\:Full\:Senior\:Yield\:*\:Revflow\:Senior\:Fee
$$

**Senior Yield % APY:**&#x20;

_The amount the Senior Tranche receives after the Revflow yield fee. This is the yield value that the Liquidity Pool receives from the Senior Tranche of a given trade._

$$
Senior\:Yield\:=\:Full\:Senior\:Yield\:-\:Revflow\:Senior\:Yield
$$

## Liquidity Pool

The Liquidity Pool is open to any investor who wishes to participate; whether they're an individual (retail), institutional/corporate, high-net worth individual or a DAO treasury. The Liquidity Pool functions as a continuous stream of capital that funds the Senior Tranche of trades, with excess liquidity being funnelled through to the Reserve which generates yield via other vetted protocols.&#x20;

Each participate in the Liquidity Pool is given an LP Token. LP Token holders can withdraw their capital from the Liquidity Pool at anytime so long as there is sufficient liquidity and healthy utilisation rates. As stated in the Senior Tranche section, holders of the LP Token will see the value of their token increase overtime as repayments and yield re-enter the Liquidity Pool, which is reflected in the LP Token's net asset value.

## Vaults

The NFT asset-backed security (i.e. the bundled-up future monthly recurring revenue subscriptions) is sent to a Vault, where it is used as collateral for a trade to be fulfilled against. Junior Tranche Investors then underwrite and fill the Junior Tranche of the trade. Once the Junior Tranche is filled, the Senior Tranche is automatically filled with capital pulled from the Liquidity Pool. Once the trade is complete, the Vault begins to accrue repayments and yield on a monthly basis until maturity (12 months). Upon maturity, the Vault automatically closes and any remaining capital (repayments and yield for the Junior Tranche) is sent back to the investor (if they have not already opted to withdraw to their wallet or redeployed the yield and repayments into the liquidity pool). Senior Tranche yield and repayments are sent back to the liquidity pool as and when they are repaid (monthly).&#x20;

## Reserve

The reserve consists of capital in the Liquidity Pool that is not being utilised in Vaults. For example, if the Liquidity Pool has $10m TVL, with $4m deployed into Vaults to fulfil trades, there is a remaining $6m that is not being utilised. To ensure maximum yield opportunities for our Liquidity Pool providers, Revflow will integrate with the leading Solana DeFi protocols to generate yield from reserve liquidity. Powered by smart contracts, reserve liquidity is funnelled into modest yield-generating protocols automatically and pulled back into the Liquidity Pool when new vaults open up for fulfilment or when additional capital is required for withdrawals. Utilisation rates will be balanced appropriately to ensure there is liquidity to fund trade flow and withdrawals.

We would like to take the opportunity to point out that each protocol will be thoroughly vetted by the Revflow team. We will utilise multiple protocols to spread risk, and we will not be hunting for the highest (and often unrealistic) yield opportunities. The reason for the reserve is to ensure that liquidity pool providers are maximising their returns on our protocol, a task not easily achieved if there is excess liquidity not being utilised. The UST fiasco saw multi-billion dollar losses for investors, with many non-crypto investors being impacted as they deposited savings into consumer-facing products promising substantial yields with little risk (15%+). Transparency on our Reserve will be one of our highest priorities, and everyone will have public viewing of yield allocations from the Reserve via [Dune Analytics](https://dune.com/home) dashboards when this feature is operational.


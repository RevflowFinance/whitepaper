# 💸 Trades and Repayments

This section will look at the flows for Trade Fulfilment and the Repayments process.

## Trades

Trades take place when a business opts to receive the yearly amount upfront from their future monthly recurring revenue. The process is as follows:&#x20;

1. A business selects how much capital they wish to obtain (the Trade Value), with the maximum being their trading limit amount. Obtainable capital will vary depending on the business's discount rate and trading limit.
2. Once confirmed and a terms sheet has been signed, the selected monthly customer contracts for the business are securitised into an asset-backed security.&#x20;
3. The asset is tokenised as an NFT on the Solana blockchain within the Revflow protocol. It is automatically locked into a new vault as collateral which opens up the Junior Tranche for investment.&#x20;
4. Junior Tranche Investors fill the Junior Tranche and receive a Junior Token. Once filled, the Senior Tranche of the trade is opened up and filled automatically by the Liquidity Pool.&#x20;
5. The vault sends the capital to the Treasury, where it is off-ramped into Fiat (USDC to USD).
6. The business receives their capital. &#x20;

## Repayments

The business will repay the total amount of the Asset Value over 12 months on a monthly basis.

1. A monthly payment is setup against the business once a trade has taken place and the capital has landed in their bank account.
2. Each month, the payment goes through for the pro-rated asset value over 12 months; i.e. the Asset Value / 12.&#x20;
3. The payment is on-ramped to Solana by exchanging USD for USDC via our Treasury. There will also be an option for businesses to pay via USDC directly.
4. The payment is sent from the Treasury to the Vault's smart contract, where it distributes the funds between the Junior Tranche and Senior Tranche.&#x20;
5. Senior Tranche repayments are sent from the Vault back to the Liquidity Pool ready for re-deployment. Junior Tranche Investors have the option of deploying the repayments into the Liquidity Pool _or_ withdrawn directly to their wallet.
6. This process repeats until the asset reaches maturity, where the Vault is then closed.&#x20;

Example start tx (comptroller deploy optimism): 0xa334c2bf31247ba6fd45715eca52f4710923b1820f90a54f64c67808c94fb599

1. DEPLOY comptroller contract
2. DEPLOY unitroller contract
3. RUN \_setPendingImplementation(address newPendingImplementation) FUNCTION IN unitroller contract WITH PARAMETERS: comptroller address
4. RUN \_become(address unitroller) FUNCTION IN comptroller contract WITH PARAMETERS: unitroller address
5. RUN \_setCloseFactor(uint256 newCloseFactorMantissa) FUNCTION IN comptroller contract THROUGH unitroller contract address WITH PARAMETERS: 500000000000000000
6. DEPLOY JumpRateModelV4 contract WITH CONSTRUCTOR PARAMETERS: 15552000, 0, 50000000000000000, 1365000000000000000, 800000000000000000, owner address, JumpRateModelV4
7. DEPLOY cErc20Immutable contracts (all of them) WITH CONSTRUCTOR PARAMETERS: underlying address, comptroller address, interestRateModel address, 200000000000000000000000000, pythPriceFeedId, name, symbol, 8, admin address
8. FOR EACH cErc20Immutable contract, RUN \_setReserveFactor(uint256 newReserveFactorMantissa) FUNCTION IN cErc20Immutable contract WITH PARAMETERS: 150000000000000000 AND RUN \_supportMarket(address cToken) FUNCTION IN comptroller contract THROUGH unitroller contract address WITH PARAMETERS: cErc20Immutable contract address
9. DEPLOY price oracle contract
10. RUN \_setPriceOracle(address newOracle) FUNCTION IN comptroller contract THROUGH unitroller contract address WITH PARAMETERS: price oracle contract address
11. RUN \_setCompSpeeds(address[] cTokens,uint256[] supplySpeeds,uint256[] borrowSpeeds) FUNCTION IN comptroller contract THROUGH unitroller contract address WITH PARAMETERS: cErc20Immutable contract address[], 0[], 0[]
12. FOR EACH cErc20Immutable contract, RUN \_setCollateralFactor(address cToken,uint256 newCollateralFactorMantissa) FUNCTION IN comptroller contract THROUGH unitroller contract address WITH PARAMETERS: cToken address, mantissa (750000000000000000 for WETH)
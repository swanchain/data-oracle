# Data Oracle

Data Oracle is a data provider DAO aiming at offer Data Oracle service for Filecoin Network. The implementation offered deal information on multi chains for users who want to store their data on Filecoin network.

Our v1 release provides the Filecoin data info available on FEVM network.

The Data Oracle provide the following fuctions:
- Data on chain proof
- Data price feed
- Node operator of data validation

Some previous work can be found here:

https://github.com/filswan/flink

https://filecoin.io/blog/posts/filecoin-and-chainlink-integration/

### FilswanOracle.sol

This is the DAO contract to sign transactions. Once a deal has enough signatures
(depending on `threshold`), the locked funds can be unlocked to the owner.

- **`updateThreshold(threshold)`** change the threshold for signatures
- **`setFilinkOracle(filinkAddress)`** change `FilinkConsumer` contract address
- **`setDAOUsers(daoUsers[])`** change the list of DAO users

- **`signCarTransaction(cidList[], dealId, network, recipient)`**  
  signs a [CAR file](https://car.ipfs.io/). Once the number of signatures reaches
  the `threshold` amount, this contract will call the `requestDealInfo` from
  `FilinkConsumer`

- **`isCarPaymentAvailable(dealId, network, recipient)`**
  returns `number of signatures >= threshold`
- **`getCarPaymentVotes(dealId, network, recipient)`**
  returns number of signatures
- **`getThreshold()`** returns `threshold`
- **`getCidList(dealId, network)`** returns `cidList` for a deal
- **`getSignatureList(dealId, network)`** returns the list of signatures for a deal

- **`preSign(dealId, network, recipient, batchCount)`**

- **`sign(dealId, network, cidList[], batchNo)`**

- **`signHash(dealId, network, recipient, voteKey)`**
- **`getHashKey(dealId, network, recipient, cidList[])`**

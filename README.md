clone from https://bitbucket.org/azazar/bitcoin-json-rpc-client/wiki/Home see detail.

Bitcoin-JSON-RPC-Client
Lightweight Java bitcoin JSON-RPC client. Without any dependencies.

Example code
```
    public static void balance() throws BitcoinException {
        System.out.println(new BitcoinJSONRPCClient().getBalance());
    }

    public static void sendCoins() throws BitcoinException {
        new BitcoinJSONRPCClient().sendToAddress("1NEYW5T2AXBBGJtTSbTtRieqkXYFY7RFno", 10);
    }

    public static void receiveCoins() throws BitcoinException {
        new BitcoinAcceptor(new BitcoinJSONRPCClient(), new ConfirmedPaymentListener() {

            @Override
            public void confirmed(Bitcoin.Transaction transaction) {
                System.out.println("Incoming transaction: amount: " + transaction.amount() + ", account: " + transaction.account());
            }

        }).run();
    }
```

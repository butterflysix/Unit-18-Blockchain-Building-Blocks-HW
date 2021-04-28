# Unit-18-Blockchain-Building-Blocks-HW

## Steps to Start the Network:
### Step One: Create Accounts for Two Nodes and Generate the Genesis Block

1. Create accounts for two nodes for the network with separate `datadir` for each using `geth`.
    * ```./geth --datadir node1 account new```
        * choose a password for node 1
            * <i> make a note of the `public address` and `secret key file` for node 1 </i>
    * ```./geth --datadir node2 account new```
        * choose a password for node 2
            * <i> make a note of the `public address` and `secret key file` for node 2 </i>
            
              | <img src="/screenshots/puppeth_config_1.jpg" width="300" height="175"> |
              |:--:|
              | [View Full Size Python Screenshot](/screenshots/puppeth_config_1.jpg)|
         
2. Generate the genesis block.
    * Open a terminal window, navigate to the `Project` folder and type the following command:
    <br>```./puppeth```
    * Type `2` to choose `Configure new genesis`
    * Type `1` to choose `Create new genesis from scratch`
    * Type `2` to choose `Clique - proof-of-authority`
    * Press "Enter" for `How many seconds should blocks take? (default = 15)`
    * Paste both addresses from the first step for `Which accounts are allowed to seal?`
    * Paste the same addresses for `Which accounts should be pre-funded?`
    * Choose `no` for pre-funding the pre-compiled accounts with wei.
    * Choose a three digit number for the Chain ID
        * <i> make a note of the Chain ID </i>
    * When you are back at the main menu, choose the `2` to `Manage existing genesis`
    * Type `2` to `Export genesis configurations`
    * Press "Enter" to save the files into the default folder
    * Exit `puppeth` by using the `Ctrl+C` keys combination

         | <img src="/screenshots/puppeth_config_2.png" width="300" height="175"> |<img src="/screenshots/puppeth_config_3.png" width="300" height="175"> |
         |:--: |:--:| 
         |[View Full Size Python Screenshot](/screenshots/puppeth_config_2.png)  |[View Full Size Python Screenshot](/screenshots/puppeth_config_3.png)|

### Step Two: Initialize the Two Nodes
1. Initialize the nodes with the genesis' json file.
    * Use `geth` to initialize each node with the `networkname.json`.
        * ```./geth --datadir node1 init networkname.json```
        * ```./geth --datadir node2 init networkname.json```
2. Begin mining the blocks with the two nodes
    * Run the nodes in separate terminal windows with the commands:
        * ```./geth --datadir node1 --unlock "SEALER_ONE_ADDRESS" --mine --rpc --allow-insecure-unlock```
        * ```./geth --datadir node2 --unlock "SEALER_TWO_ADDRESS" --mine --port 30304 --bootnodes"enode://SEALER_ONE_ENODE_ADDRESS@127.0.0.1:30303" --ipcdisable --allow-insecure unlock```
            * <i> be sure to unlock the accounts after running each command </i>
            
    * The blockchain should now be running
### Step Three: Send a Test Transaction
1. Open MyCrypto
2. Select "Change Network"
3. Select "Add Custom Node"
4. Input your network name in the "Node Name" box
5. Select "Custom" in the "Network" dropdown
6. Input your network name in "Network Name"
7. Input "ETH" in the "Currency" box
8. Input your chain ID number in "Chain ID"
9. Input "http://127.0.0.1:8545" for URL
10. Select "Save and Use Custom Node"
### Step Four: Send a Transaction
1. Open MyCrypto
2. Select "View & Send"
3. Select "Private Key" sign in option
4. Import the keystore file from the `node1/keystore` directory into MyCrypto. This will import the private key.
5. Enter the password
6. Select "Unlock"
7. Send a transaction from `node1` account to the `node2` account
8. Input the amount of currency
9. Select "Send Transaction"
10. Write down "TX Hash"

      | <img src="/screenshots/mycrypto_tx_status.png" width="300" height="175"> |
      |:--:|
      |[View Full Size MyCrypto Screenshot](/screenshots/mycrypto_tx_status.png)|

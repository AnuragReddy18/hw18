## Blockchain Installation Guide
# Installing MyCrypto App
-	Navigate to https://download.mycrypto.com
-	Download MyCrypto
# Installing Go Ethereum tools
- Navigate to https://geth.ethereum.org/downloads/
- Download Geth & Tools 1.10.15
- Put unarchived folder in home directory as Blockchain-Tools
# Creating Nodes
- Empty directory for nodes
  - mkdir node1 node2
- New account numbers from nodes to use as signers
  - ./geth account new –datadir node1
  -	./geth account new –datadir node2
- Password for node1 and node2
  -	echo 'node1pswd' > node1/password.txt
  -	echo 'node2pswd' > node2/password.txt
  -	echo 'NODE1adress' >> accounts.txt
  -	echo 'NODE2adress' >> accounts.txt
# Running Puppeth
- 	Start puppeth
  -	./puppet in Blockchain-Tools
  -	>zbashtestwallet <- name of network
  -	Type 2 to pick the Configure new genesis option, then 1 to Create new genesis from scratch
  -	Type 1 to choose Proof of Work
  -	Addresses: Uses those assocated with cloud mneumonic Use MyCrypto
  -	Continue with default option for the prompts to prefund
  -	Chain ID: come up with a number
  -	In the puppeth prompt, navigate to the Manage existing genesis by typing 2 and hit enter
  -	Next, type 2 again to choose the Export genesis configurations option
  -	Show files in Blockchain-Tools folder. Show json file
  -	Exit the puppeth prompt by using the Ctrl+C keys combination.
# Starting the Blockchain
  -	Initialize nodes
  -	./geth init puppernet.json --datadir node1
  -	./geth init puppernet.json --datadir node2
-	Make first node a miner
  -	./geth --datadir node1 --mine --minerthreads 1 --unlock "NODE1_address" --password node1/password.txt  --rpc --allow-insecure-unlock
  -	copy the entire enode:// address (including the last @address:port segment) of the first node located in the Started P2P Networking line:
-	Launch second node
  -	./geth --datadir node2 --unlock "NODE2_address" --mine --port 30305 --bootnodes enode://YOUR_ENDCODE_FROM_NODE1 --password node2/password.txt  --allow-insecure-unlock
# Setting Network info on Mycrypto
- 	Click on “Add Custom Node”, then add the custom network information that was set in the genesis.
- 		Ensure that I scroll down to choose Custom in the "Network" setting to reveal more options like Chain ID:
- 	The chain ID must match what I came up with earlier.
- 	The URL is pointing to the default RPC port on my local machine. Everyone should use this same URL: http://127.0.0.1:8545. Click on the "Save & Use Custom Node" button, to use the network; double-check that it is selected and is connected. 
- 	Import the keystore file from th e node1/keystore directory into MyCrypto. This will import the private key.
- 	Send a transaction from the node1 account to the node2 account.
- 	Copy the transaction hash and paste it into the “TX Status” section of the app, or click “TX Status” in the popup.
- 	The transaction is should now read Succesfull! C with the metadata (status, tx hash, block number, etc).
- 	Done!


## Blockchain Installation Guide
# Installing MyCrypto App
-	Navigate to https://download.mycrypto.com
-	Download MyCrypto
# Installing Go Ethereum tools
a.	Navigate to https://geth.ethereum.org/downloads/
b.	Download Geth & Tools 1.10.15
c.	Put unarchived folder in home directory as Blockchain-Tools
# Creating Nodes
a.	Empty directory for nodes
i.	mkdir node1 node2
b.	New account numbers from nodes to use as signers
i.	./geth account new –datadir node1
ii.	./geth account new –datadir node2
c.	Password for node1 and node2
i.	echo 'node1pswd' > node1/password.txt
ii.	echo 'node2pswd' > node2/password.txt
iii.	echo 'NODE1adress' >> accounts.txt
iv.	echo 'NODE2adress' >> accounts.txt
# Running Puppeth
a.	Start puppeth
i.	./puppet in Blockchain-Tools
ii.	>zbashtestwallet <- name of network
iii.	Type 2 to pick the Configure new genesis option, then 1 to Create new genesis from scratch
iv.	Type 1 to choose Proof of Work
v.	Addresses: Uses those assocated with cloud mneumonic Use MyCrypto
vi.	Continue with default option for the prompts to prefund
vii.	Chain ID: come up with a number
viii.	In the puppeth prompt, navigate to the Manage existing genesis by typing 2 and hit enter
ix.	Next, type 2 again to choose the Export genesis configurations option
x.	Show files in Blockchain-Tools folder. Show json file
xi.	Exit the puppeth prompt by using the Ctrl+C keys combination.
# Starting the Blockchain
a.	Initialize nodes
i.	./geth init puppernet.json --datadir node1
ii.	./geth init puppernet.json --datadir node2
b.	Make first node a miner
i.	./geth --datadir node1 --mine --minerthreads 1 --unlock "NODE1_address" --password node1/password.txt  --rpc --allow-insecure-unlock
ii.	copy the entire enode:// address (including the last @address:port segment) of the first node located in the Started P2P Networking line:
c.	Launch second node
i.	./geth --datadir node2 --unlock "NODE2_address" --mine --port 30305 --bootnodes enode://YOUR_ENDCODE_FROM_NODE1 --password node2/password.txt  --allow-insecure-unlock
# Setting Network info on Mycrypto
a.	Click on “Add Custom Node”, then add the custom network information that was set in the genesis.
b.	Ensure that I scroll down to choose Custom in the "Network" setting to reveal more options like Chain ID:
c.	The chain ID must match what I came up with earlier.
d.	The URL is pointing to the default RPC port on my local machine. Everyone should use this same URL: http://127.0.0.1:8545. Click on the "Save & Use Custom Node" button, to use the network; double-check that it is selected and is connected. 
e.	Import the keystore file from th e node1/keystore directory into MyCrypto. This will import the private key.
f.	Send a transaction from the node1 account to the node2 account.
g.	Copy the transaction hash and paste it into the “TX Status” section of the app, or click “TX Status” in the popup.
h.	The transaction is should now read Succesfull! C with the metadata (status, tx hash, block number, etc).
i.	Done!


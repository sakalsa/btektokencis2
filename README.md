# Build the contract

cargo concordium build --out dist/fungible/module.wasm.v1 --schema-out dist/fungible/schema.bin

**Schema Embedded to Module** cargo concordium build --schema-embed --out dist/embedded/module.wasm.v1

# Deploy the contract

concordium-client module deploy dist/fungible/module.wasm.v1 --sender YOUR-ACCOUNT --name YOUR-CONTRACT-NAME --grpc-port 10000 --grpc-ip node.testnet.concordium.com

.\concordium-client module deploy dist/fungible/module.wasm.v1 --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --name btek --grpc-ip 178.33.148.36

**Embedded Schema**
If you are using schema embedded to module, remove "--schema param" inputs from the commands!

# Initialize the contract

concordium-client contract init MODULE-HASH --sender YOUR-ACCOUNT --energy 30000 --contract fungible-cis2 --grpc-port 10000 --grpc-ip node.testnet.concordium.com

.\concordium-client contract init e92b60d15c339deae3109f67a8688c5b988b8fac7119fab4cb92bea47e9cf4b9 --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 30000 --contract fungible-cis2 --grpc-port 10000 --grpc-ip 178.33.148.36

# Mint Fungible Tokens

concordium-client contract update YOUR-CONTRACT-INSTANCE --entrypoint mint --parameter-json token-artifacts/mint-params.json --schema dist/fungible/schema.bin --sender YOUR-ACCOUNT --energy 6000 --grpc-port 10000 --grpc-ip node.testnet.concordium.com

.\concordium-client contract update 9364 --entrypoint mint --parameter-json token-artifacts/mint-params.json --schema dist/fungible/schema.bin --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 6000 --grpc-ip 178.33.148.36

# View Contract State

concordium-client contract invoke YOUR-CONTRACT-INSTANCE --entrypoint view --schema dist/fungible/schema.bin --grpc-port 10000 --grpc-ip node.testnet.concordium.com

.\concordium-client contract invoke 9364 --entrypoint view --schema dist/fungible/schema.bin --grpc-ip 178.33.148.36

# Check Metadata

concordium-client contract invoke YOUR-INDEX --entrypoint tokenMetadata --parameter-json token-artifacts/ids.json --schema dist/fungible/schema.bin --grpc-port 10001

.\concordium-client contract invoke 9364 --entrypoint tokenMetadata --parameter-json token-artifacts/ids.json --schema dist/fungible/schema.bin --grpc-ip 178.33.148.36

# Transfer

.\concordium-client contract update YOUR-INDEX --entrypoint transfer --parameter-json token-artifacts/transfer.json --schema dist/fungible/schema.bin --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 6000 --grpc-ip 178.33.148.36

concordium-client contract update 9364 --entrypoint transfer --parameter-json token-artifacts/transfer.json --schema dist/fungible/schema.bin --sender YOUR-ACCOUNT --energy 6000 --grpc-port 10000 --grpc-ip node.testnet.concordium.com

# Burn

concordium-client contract update YOUR-INDEX --entrypoint burn --parameter-json token-artifacts/burn.json --schema dist/fungible/schema.bin --sender YOUR-ACCOUNT --energy 6000 --grpc-port 10000 --grpc-ip node.testnet.concordium.com

.\concordium-client contract update 9364--entrypoint burn --parameter-json token-artifacts/burn.json --schema dist/fungible/schema.bin --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 6000 --grpc-ip 178.33.148.36




*******************************************************************
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client module deploy dist/fungible/module.wasm.v1 --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --name btek --grpc-ip 178.33.148.36              
Using default energy amount of 97679 NRG.
Deploy the module 'dist/fungible/module.wasm.v1' and name it 'btek'.
Allowing up to 97679 NRG to be spent as transaction fee.
Confirm [yN]: y
y
Deploying module...
Enter password for credential with index 0 and signing key with index 0:
Transaction 'e92b60d15c339deae3109f67a8688c5b988b8fac7119fab4cb92bea47e9cf4b9' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status e92b60d15c339deae3109f67a8688c5b988b8fac7119fab4cb92bea47e9cf4b9'.
[21:30:33] Waiting for the transaction to be committed.....
Transaction is finalized into block a32a4f0db7dd3f94427baa76cc005a9eff459c59700bc2883258eee202ff65c6 with status "success" and cost 266.077188 CCD (97678 NRG).
[21:30:37] Transaction finalized.
Module successfully deployed with reference: '1d42845e9412761eab438886459c9acc94170062b2fa248aeef3a6cbc3136d6e'.
Module reference 1d42845e9412761eab438886459c9acc>                                                                                                                                                  
PS C:\Users\User\Github Clones\ccd1\btektokencis2> 
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract init e92b60d15c339deae3109f67a8688c5b988b8fac7119fab4cb92bea47e9cf4b9 --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 30000 --contract fungible-cis2 --grpc-port 10000 --grpc-ip 178.33.148.36
Error: GRPC response with status 'UNIMPLEMENTED': GRPC error: not enough bytes.
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract init e92b60d15c339deae3109f67a8688c5b988b8fac7119fab4cb92bea47e9cf4b9 --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 30000 --contract fungible-cis2 --grpc-ip 178.33.148.36                  
Error: The module reference 'e92b60d15c339deae3109f67a8688c5b988b8fac7119fab4cb92bea47e9cf4b9' does not exist in block best block.
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract init 1d42845e9412761eab438886459c9acc94170062b2fa248aeef3a6cbc3136d6e --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 30000 --contract fungible-cis2 --grpc-ip 178.33.148.36
Initialize contract 'fungible-cis2' from module '1d42845e9412761eab438886459c9acc94170062b2fa248aeef3a6cbc3136d6e' with no parameters. Sending 0.000000 CCD.
Allowing up to 30000 NRG to be spent as transaction fee.
Transaction expires on Mon,  7 Aug 2023 18:44:54 UTC.
Confirm [yN]: y
y
Enter password for credential with index 0 and signing key with index 0: 
Transaction '422493ffb4db2e3194ca6545cd46585534c7915c79a2f8a0fc1ee31f80abaf28' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status 422493ffb4db2e3194ca6545cd46585534c7915c79a2f8a0fc1ee31f80abaf28'.
[21:35:03] Waiting for the transaction to be committed.......
Transaction is finalized into block b65b028c1766ecb2230a52e607e472700a6b7f8ae59d58c50f66fece78984a3f with status "success" and cost 7.267696 CCD (2668 NRG).
[21:35:12] Transaction finalized.
Contract successfully initialized with address: {"index":9364,"subindex":0}
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract update btek --entrypoint mint --parameter-json token-artifacts/mint-params.json --schema dist/fungible/schema.bin --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 6000 --grpc-ip 178.33.148.36
Error: 'btek' is neither the address index nor the name of a contract.
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract update 9364 --entrypoint mint --parameter-json token-artifacts/mint-params.json --schema dist/fungible/schema.bin --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 6000 --grpc-ip 178.33.148.36
Update contract 'fungible-cis2' using the function 'mint' with JSON parameters from 'token-artifacts/mint-params.json'. Sending 0.000000 CCD.
Allowing up to 6000 NRG to be spent as transaction fee.
Transaction expires on Mon,  7 Aug 2023 18:48:34 UTC.
Confirm [yN]: y
y
Enter password for credential with index 0 and signing key with index 0: 
Transaction 'd4b742a135e791dd2d34163d3315c893a88ad9804b42ba662a55c5ff6f2e2fd6' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status d4b742a135e791dd2d34163d3315c893a88ad9804b42ba662a55c5ff6f2e2fd6'.
[21:38:42] Waiting for the transaction to be committed...........
Transaction is finalized into block 28f984ab3295d9ab9ace804fa4bf624ed287d44a7a932bb96f7bd9b1e89a3c2c with status "success" and cost 10.217813 CCD (3751 NRG).
[21:38:59] Transaction finalized.
Successfully updated contract instance {"index":9364,"subindex":0} using the function 'mint'.
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract invoke 9364 --entrypoint view --schema dist/fungible/schema.bin --grpc-ip 178.33.148.36
Invocation resulted in success:
 - Energy used: 2331 NRG 
 - Return value:
      {
          "state": [
              [
                  {
                      "Account": [
                          "4beJ8DrzYT4rWBRUy8qdafyfuknjMbXdXDNXtHoUd9vEsFDnGb"
                      ]
                  },
                  {
                      "balances": [
                          [
                              "01",
                              "5000"
                          ]
                      ],
                      "operators": []
                  }
              ]
          ],
          "tokens": [
              [
                  "01",
                  {
                      "circulating_supply": "5000",
                      "max_supply": "10000"
                  }
              ]
          ]
      }
 .
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract update YOUR-INDEX --entrypoint transfer --parameter-json token-artifacts/transfer.json --schema dist/fungible/schema.bin --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 6000 --grpc-ip 178.33.148.36
Error: 'YOUR-INDEX' is neither the address index nor the name of a contract.
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract update 9364 --entrypoint transfer --parameter-json token-artifacts/transfer.json --schema dist/fungible/schema.bin --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 6000 --grpc-ip 178.33.148.36      
Update contract 'fungible-cis2' using the function 'transfer' with JSON parameters from 'token-artifacts/transfer.json'. Sending 0.000000 CCD.
Allowing up to 6000 NRG to be spent as transaction fee.
Transaction expires on Mon,  7 Aug 2023 18:53:23 UTC.
Confirm [yN]: y
y
Enter password for credential with index 0 and signing key with index 0: 
Transaction '1167af31700e5381433c04ff849a3e7f67877596f0d437530229ad637ebb4e21' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status 1167af31700e5381433c04ff849a3e7f67877596f0d437530229ad637ebb4e21'.
[21:43:31] Waiting for the transaction to be committed.......................
Transaction is finalized into block 5feffbfa6d3436e040f1983ad95b62f8ca3e3397ae619c1c3154adc9af7a9d72 with status "rejected" and cost 6.594862 CCD (2421 NRG).
Transaction rejected: 'transfer' in 'fungible-cis2' at {"index":9364,"subindex":0} failed with code -42000003.
[21:44:12] Transaction finalized.
Error: Updating contract instance failed:
       'transfer' in 'fungible-cis2' at {"index":9364,"subindex":0} failed with code -42000003.
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract update 9364--entrypoint burn --parameter-json token-artifacts/burn.json --schema dist/fungible/schema.bin --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 6000 --grpc-ip 178.33.148.36
Invalid argument `burn'

Usage: concordium-client.exe contract update
         INDEX-OR-NAME [--subindex SUBINDEX] --entrypoint ENTRYPOINT-NAME
         [--parameter-json FILE | --parameter-binary FILE] [--schema SCHEMA] [--amount CCD-AMOUNT]
         [--sender SENDER] [--alias ALIAS] [--keys KEYS] [--signers SIGNERS] [--nonce NONCE]
         --energy MAX-ENERGY [--expiry EXPIRY] [--no-confirm] [--no-wait]

  Update an existing contract.
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract update 9364 --entrypoint burn --parameter-json token-artifacts/burn.json --schema dist/fungible/schema.bin --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 6000 --grpc-ip 178.33.148.36
Update contract 'fungible-cis2' using the function 'burn' with JSON parameters from 'token-artifacts/burn.json'. Sending 0.000000 CCD.
Allowing up to 6000 NRG to be spent as transaction fee.
Transaction expires on Mon,  7 Aug 2023 18:56:32 UTC.
Confirm [yN]: y
y
Enter password for credential with index 0 and signing key with index 0: 
Transaction 'ebf077440f7625729d489cccd2189d8ba21596d598f641206a63c25cf48eecc6' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status ebf077440f7625729d489cccd2189d8ba21596d598f641206a63c25cf48eecc6'.
[21:46:39] Waiting for the transaction to be committed.......
Transaction is finalized into block 8586edb649d76ee20673875be215b8236036c525e4c83e63c6f6f02266de94fd with status "rejected" and cost 6.475005 CCD (2377 NRG).
Transaction rejected: 'burn' in 'fungible-cis2' at {"index":9364,"subindex":0} failed with code -9.
[21:46:47] Transaction finalized.
Error: Updating contract instance failed:
       'burn' in 'fungible-cis2' at {"index":9364,"subindex":0} failed with code -9.
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract invoke 9364 --entrypoint tokenMetadata --parameter-json token-artifacts/ids.json --schema dist/fungible/schema.bin --grpc-ip 178.33.148.36                                                                          
Invocation resulted in success:
 - Energy used: 2261 NRG
 - Return value:
      [
          {
              "hash": {
                  "None": []
              },
              "url": "https://gateway.pinata.cloud/ipfs/QmfVuCYLoSWtvZe3UmRrStbT1vzyYxuFCfpxZ6bzLpNiYh"
          }
      ]
 .
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract update 9364 --entrypoint transfer --parameter-json token-artifacts/transfer.json --schema dist/fungible/schema.bin --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 6000 --grpc-ip 178.33.148.36
Update contract 'fungible-cis2' using the function 'transfer' with JSON parameters from 'token-artifacts/transfer.json'. Sending 0.000000 CCD.
Allowing up to 6000 NRG to be spent as transaction fee.
Transaction expires on Mon,  7 Aug 2023 19:07:15 UTC.
Confirm [yN]: y
y
Enter password for credential with index 0 and signing key with index 0: 
Transaction '2ba382f2958b0f524a9c2aeea56e60baaa1e6450ef4c3c7d7a465ddd795f932e' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status 2ba382f2958b0f524a9c2aeea56e60baaa1e6450ef4c3c7d7a465ddd795f932e'.
[21:57:23] Waiting for the transaction to be committed....
Transaction is finalized into block 853bdef5e4da79ef4e846c7ae3d35449bf8188568205699a391f8783644a0de9 with status "rejected" and cost 6.589414 CCD (2419 NRG).
Transaction rejected: 'transfer' in 'fungible-cis2' at {"index":9364,"subindex":0} failed with code -42000003.
[21:57:26] Transaction finalized.
Error: Updating contract instance failed:
       'transfer' in 'fungible-cis2' at {"index":9364,"subindex":0} failed with code -42000003.
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract update 9364 --entrypoint transfer --parameter-json token-artifacts/transfer.json --schema dist/fungible/schema.bin --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 6000 --grpc-ip 178.33.148.36
Update contract 'fungible-cis2' using the function 'transfer' with JSON parameters from 'token-artifacts/transfer.json'. Sending 0.000000 CCD.
Allowing up to 6000 NRG to be spent as transaction fee.
Transaction expires on Mon,  7 Aug 2023 19:12:32 UTC.
Confirm [yN]: y
y
Enter password for credential with index 0 and signing key with index 0: 
Transaction 'bb1bc583833d5827132984bd49e041ea4bc0f940a4f6113bd81e236ff2acf642' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status bb1bc583833d5827132984bd49e041ea4bc0f940a4f6113bd81e236ff2acf642'.
[22:02:39] Waiting for the transaction to be committed.........
Transaction is finalized into block b23e78b6f465a0bcf22de0608cbbf94426eb8366c95b8d9a38f2e26b571f97b4 with status "success" and cost 8.549665 CCD (3137 NRG).
[22:02:52] Transaction finalized.
Successfully updated contract instance {"index":9364,"subindex":0} using the function 'transfer'.
PS C:\Users\User\Github Clones\ccd1\btektokencis2> .\concordium-client contract update 9364 --entrypoint burn --parameter-json token-artifacts/burn.json --schema dist/fungible/schema.bin --sender 3jhnM48FtLk46n74roAqmLqzauedzph8cGjYC2yDHxL7CUmGdt --energy 6000 --grpc-ip 178.33.148.36
Update contract 'fungible-cis2' using the function 'burn' with JSON parameters from 'token-artifacts/burn.json'. Sending 0.000000 CCD.
Allowing up to 6000 NRG to be spent as transaction fee.
Transaction expires on Mon,  7 Aug 2023 19:13:02 UTC.
Confirm [yN]: y
y
Enter password for credential with index 0 and signing key with index 0: 
Transaction '9967da931ea2a81acc6c5e8ae1cd4600acde68b9e00604870a3dbe3ed20c040f' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status 9967da931ea2a81acc6c5e8ae1cd4600acde68b9e00604870a3dbe3ed20c040f'.
[22:03:08] Waiting for the transaction to be committed...........
Transaction is finalized into block 46f622bf22773f8d6d8cb37e9f7f71eee017cb953b2683f30e4dbb6a1f241316 with status "success" and cost 7.609392 CCD (2792 NRG).
[22:03:25] Transaction finalized.
Successfully updated contract instance {"index":9364,"subindex":0} using the function 'burn'.
PS C:\Users\User\Github Clones\ccd1\btektokencis2> 
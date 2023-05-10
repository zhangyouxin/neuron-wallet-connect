
This proposla is for the neuron wallet to communicate with dapps.

 - namespace: ckb
 - chains: 
   - ckb:mainnet-1-1 for `m/44'/309'/0'` with SECP256K1_BLAKE160 locks (for both external and internal addresses)
   - ckb:testnet-1-1 
   - ckb:mainnet-1-2 for `m/44'/309'/0'` with OMNI locks with owner mode (considering some dapps already uses this lock)
   - ckb:testnet-1-2
   - // more chains to be added
 - methods:
   - wallet_signData // signs data with a "Nervos Message:" prefix in ASCII use current connected address private key
     - payload: HexString // 0x...
   - wallet_signTransaction // signs the transaction where input cells belong to current address
     - payload: `Transaction` type of `@ckb-lumos/base`
   - address_sign_in ??
   - address_sign_out ??
 - events:
   - connected, with data (networkInfo, address) 
   - disconnected, with data (reason) 
   - address_changed, with data (networkInfo) 
   - network_changed, with data (address) 
# 🏗️ Multi-Sig Wallet Challenge - Complete Guide

## ✅ Configuration Completed

The following configurations have been set up for you:

1. ✅ **Deploy script updated** - Uses dynamic chainId and deployer address as first signer
2. ✅ **Network configured** - Set to Sepolia testnet
3. ✅ **Frontend configured** - Set to Sepolia network
4. ✅ **Burner wallet enabled** - Works on all chains (not just localhost)
5. ✅ **Environment files created** - Basic .env.local file created
6. ✅ **Deployer account generated** - Address: `0xBcc566fEBDcB348A00841d167C0457294f96Ce65`

---

## 📋 Checkpoint 1: Configure Owners 🖋

### Step 1: Check Your Deployer Balance

```bash
yarn account
```

### Step 2: Fund Your Deployer Account

- Your deployer address: `0xBcc566fEBDcB348A00841d167C0457294f96Ce65`
- Get Sepolia ETH from faucets:
  - https://sepoliafaucet.com/
  - https://www.alchemy.com/faucets/ethereum-sepolia
  - https://cloud.google.com/application/web3/faucet/ethereum/sepolia

### Step 3: Deploy Contract (Local Testing First)

For local testing:

```bash
# Terminal 1 - Start local blockchain
yarn chain

# Terminal 2 - Deploy contract
yarn deploy --reset

# Terminal 3 - Start frontend
yarn start
```

### Step 4: Configure Additional Owners

1. Open http://localhost:3000
2. Go to "Owners" tab
3. Fill the form to add new owners:
   - Add Owner Address
   - Set number of signatures required
4. Click "Create Tx"
5. Sign and execute the transaction

---

## 💸 Checkpoint 2: Transfer Funds

### Step 1: Fund Your Multisig Contract

1. Find your multisig contract address in "Multisig" or "Debug Contracts" tab
2. Use the faucet to send ETH to your multisig contract

### Step 2: Create Transfer Transaction

1. Go to "Create" tab
2. Fill in:
   - **To Address**: Recipient address
   - **Amount**: Amount of ETH to send
   - **Function**: Leave empty for simple transfer
3. Click "Create Tx"

### Step 3: Get Required Signatures

1. Open transaction in "Pool" tab
2. If you need multiple signatures, open another browser/wallet
3. Sign with required number of owners

### Step 4: Execute Transaction

1. Once enough signatures collected, click "Exec"
2. Transaction will be marked as "Completed" in "Pool" tab
3. View in "Multisig" tab with all executed transactions

---

## 🛰 Checkpoint 3: Deploy to Public Network

### Step 1: Update Your Frontend Address (Optional)

If you want to use a specific address as the first signer instead of the deployer:

```typescript
// In packages/hardhat/deploy/00_deploy_meta_multisig_wallet.ts
// Replace the args line with:
args: [chainId, ["YOUR_WALLET_ADDRESS_HERE"], 1],
```

### Step 2: Switch Network (If Needed)

The project is already configured for Sepolia. To use a different network:

**In `packages/hardhat/hardhat.config.ts`:**

```typescript
defaultNetwork: "optimismSepolia", // or "baseSepolia", etc.
```

**In `packages/nextjs/scaffold.config.ts`:**

```typescript
targetNetworks: [chains.optimismSepolia], // or chains.baseSepolia, etc.
```

### Step 3: Deploy to Public Network

```bash
# Make sure your deployer is funded on Sepolia
yarn account

# Deploy to the network
yarn deploy --network sepolia
# OR if you changed defaultNetwork, just:
yarn deploy
```

### Step 4: Start Frontend

```bash
yarn start
```

Visit http://localhost:3000 and verify you see Sepolia network.

---

## 🚢 Checkpoint 4: Ship Your Frontend

### Step 1: Install Vercel CLI (If Not Installed)

```bash
npm i -g vercel
```

### Step 2: Deploy to Vercel

```bash
# First time login
yarn vercel:login

# Deploy to preview URL
yarn vercel

# Deploy to production URL
yarn vercel --prod
```

### Step 3: Configure Environment Variables in Vercel

After deployment, add these in Vercel Dashboard:

- `NEXT_PUBLIC_ALCHEMY_API_KEY` - Your Alchemy API key
- `NEXT_PUBLIC_WALLET_CONNECT_PROJECT_ID` - Your WalletConnect project ID

### Step 4: Get Your Own API Keys (Production)

**Alchemy API Key:**

1. Go to https://dashboard.alchemyapi.io
2. Create account and get API key
3. Add to `packages/hardhat/.env`:
   ```
   ALCHEMY_API_KEY=your_key_here
   ```
4. Add to Vercel environment variables

**Etherscan API Key:**

1. Go to https://etherscan.io/myapikey
2. Create account and get API key
3. Add to `packages/hardhat/.env`:
   ```
   ETHERSCAN_V2_API_KEY=your_key_here
   ```

**WalletConnect Project ID:**

1. Go to https://cloud.walletconnect.com
2. Create project and get ID
3. Add to Vercel environment variables

---

## 📜 Checkpoint 5: Contract Verification

### Step 1: Verify Contract on Etherscan

```bash
# Verify on Sepolia
yarn verify --network sepolia

# Or for other networks
yarn verify --network optimismSepolia
```

### Step 2: Share Your Multisig

1. Get your public Vercel URL
2. Share with friends to add as signers
3. Send ETH through the multisig! 🎉

---

## 🔧 Troubleshooting

### Issue: "Insufficient funds for gas"

**Solution:** Fund your deployer account with ETH from a faucet

### Issue: "Contract already deployed"

**Solution:** Run `yarn deploy --reset` to deploy fresh contract

### Issue: "Wrong network"

**Solution:** Make sure both `hardhat.config.ts` and `scaffold.config.ts` use the same network

### Issue: "Can't connect wallet"

**Solution:**

- Check MetaMask is on correct network
- Try using burner wallet (now enabled on all chains)

### Issue: "Transaction not showing in pool"

**Solution:** Make sure the backend pool server is running (it starts automatically with `yarn start`)

---

## 📝 Quick Command Reference

```bash
# Generate deployer account
yarn generate

# Check account balance
yarn account

# Start local chain
yarn chain

# Deploy contract (local)
yarn deploy --reset

# Deploy to network
yarn deploy --network sepolia

# Start frontend
yarn start

# Verify contract
yarn verify --network sepolia

# Deploy frontend
yarn vercel --prod
```

---

## 🎯 Success Criteria

- ✅ Contract deployed to public testnet
- ✅ Multiple owners configured
- ✅ Signatures required set to 2+
- ✅ Successfully transferred funds via multisig
- ✅ Contract verified on Etherscan
- ✅ Frontend deployed to Vercel
- ✅ Shared with friends to test multisig functionality

---

## 🚀 Next Steps

After completing all checkpoints:

1. Share your deployed multisig URL
2. Add multiple signers (friends/team members)
3. Practice creating and signing transactions
4. Experiment with different signature thresholds
5. Try deploying on mainnet with real assets (be careful!)

---

## 📚 Additional Resources

- [Scaffold-ETH 2 Documentation](https://docs.scaffoldeth.io/)
- [Hardhat Documentation](https://hardhat.org/docs)
- [OpenZeppelin Contracts](https://docs.openzeppelin.com/contracts)
- [Multi-Sig Wallet Pattern](https://ethereum.org/en/developers/docs/smart-contracts/security/)

---

**Good luck with your Multi-Sig Wallet challenge! 🎉**

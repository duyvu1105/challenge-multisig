# Multi-Sig Wallet - Quick Start Commands

## 🚀 For Local Development (Testing)

### Terminal 1 - Start Local Blockchain

```bash
yarn chain
```

### Terminal 2 - Deploy Contract

```bash
yarn deploy --reset
```

### Terminal 3 - Start Frontend

```bash
yarn start
```

Then open: http://localhost:3000

---

## 🌐 For Sepolia Testnet Deployment

### Step 1: Fund Your Deployer

Your deployer address: **0xBcc566fEBDcB348A00841d167C0457294f96Ce65**

Get Sepolia ETH from:

- https://sepoliafaucet.com/
- https://www.alchemy.com/faucets/ethereum-sepolia
- https://cloud.google.com/application/web3/faucet/ethereum/sepolia

### Step 2: Check Balance

```bash
yarn account
```

### Step 3: Deploy to Sepolia

```bash
yarn deploy
```

(Network is already configured to Sepolia)

### Step 4: Start Frontend

```bash
yarn start
```

### Step 5: Verify Contract

```bash
yarn verify --network sepolia
```

---

## 📦 Deploy Frontend to Vercel

```bash
# Login to Vercel
yarn vercel:login

# Deploy to production
yarn vercel --prod
```

---

## 🔑 Important Notes

1. **Your Deployer Address:** `0xBcc566fEBDcB348A00841d167C0457294f96Ce65`
2. **Current Network:** Sepolia (configured in both hardhat and frontend)
3. **Burner Wallet:** Enabled on all chains
4. **First Signer:** Set to deployer address (can be changed in deploy script)

---

## 📁 Configuration Files Changed

✅ `packages/hardhat/deploy/00_deploy_meta_multisig_wallet.ts` - Uses dynamic chainId and deployer
✅ `packages/hardhat/hardhat.config.ts` - defaultNetwork set to "sepolia"
✅ `packages/nextjs/scaffold.config.ts` - targetNetworks set to sepolia, burner wallet enabled
✅ `packages/nextjs/.env.local` - Created with default API keys

---

## 🎯 Next Steps

1. ✅ Fund your deployer account on Sepolia
2. ✅ Deploy contract: `yarn deploy`
3. ✅ Start frontend: `yarn start`
4. ✅ Add more owners via the "Owners" tab
5. ✅ Create and execute multi-sig transactions
6. ✅ Deploy to Vercel: `yarn vercel --prod`
7. ✅ Verify contract: `yarn verify --network sepolia`

---

For detailed instructions, see **CHECKPOINT_GUIDE.md**

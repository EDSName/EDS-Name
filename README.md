# .EDS Name
![eds name](https://github.com/user-attachments/assets/7793727b-d7a7-4b06-b386-fcb0bea970ce)

> **Your Identity. Your Name. Your Web3.**

Transform cryptographic addresses into memorable human-readable names on the Endless blockchain. Own your digital identity as an NFT.

**Live Platform:** https://eds-name.netlify.app

---

## What Is .EDS Name?

.EDS Name is a decentralized naming service built natively on the Endless blockchain using Move smart contracts. We solve Web3's biggest UX problem: nobody can remember `0x742d35Cc6634C0532925a3b844Bc9e7595f0bEb`.

**With .EDS, you become simply `alice.eds`**

Every `.eds` domain is minted as an NFT that you fully own. Trade it, sell it, or keep it forever. Your name, your rules.

---

## Why We Built This

**The Problem:**
- Blockchain addresses are impossible to remember
- Sending funds requires copying/pasting long hex strings
- One typo = lost funds forever
- No human-friendly identity layer for Web3

**Our Solution:**
- Register memorable `.eds` names in seconds
- Each domain is a tradeable NFT on Endless blockchain
- Built-in marketplace for buying/selling premium names
- Referral system that rewards community growth
- Native integration with Endless Wallet

**This isn't just a naming service — it's the foundation for Web3 identity on Endless.**

---

## What You Can Do Right Now

### 🎯 Register Your Domain
Search for any name, connect your Endless wallet, and register it instantly. Domains are minted as NFTs directly on-chain.

**Pricing:** Transparent on-chain pricing with no hidden fees
**Ownership:** Permanent ownership — domains don't expire

### 🏪 Trade on the Marketplace
List your domains for sale at any price. Browse and purchase premium names from other users. All transactions happen on-chain with automatic seller payouts.

**Features:**
- Fixed price listings
- Browse all registered domains
- Filter by price, length, or registration date
- Instant transfers after purchase

### 🎁 Earn Through Referrals
Share your referral code and earn **10% commission** on every domain registered by people you refer.

Referrals only work if you already own at least one domain. Commissions are paid automatically via smart contract.

### 📊 Dashboard & Analytics
Track everything you own and earn:
- All your registered domains
- Active marketplace listings
- Referral statistics and earnings
- Transaction history

---

## How It Works

### The Flow

1. **User searches for a domain** → Frontend checks availability via backend
2. **Domain is available** → Backend generates metadata and NFT card → Uploads to IPFS
3. **User confirms transaction** → Endless wallet signs the transaction → Domain is minted on-chain
4. **Transaction completes** → Backend indexes the domain in Firebase → User receives NFT in wallet
5. **Domain is active** → Appears in dashboard and marketplace → Fully tradeable

### Smart Contract Architecture

Our Move contracts implement:
- **NFT Standard:** Each domain is an ERC-721-like token
- **Registry System:** Global mapping of names → addresses
- **Marketplace Logic:** On-chain listing, offers, and transfers
- **Referral Tracking:** Commission calculation and distribution
- **Event Emission:** Every action is logged on-chain

```move
module endless_addr::domain_registry {
    struct Domain has key, store {
        name: String,
        owner: address,
        metadata_uri: String,
        registered_at: u64,
    }
    
    public entry fun register_domain(
        account: &signer,
        name: String,
        metadata_uri: String
    ) { ... }
}
```

---

## Current Features (Production Ready)

### ✅ Domain Registration
- Instant availability checking
- Real-time pricing calculation
- Automatic NFT card generation (SVG/PNG)
- IPFS metadata upload
- On-chain minting via Endless wallet
- Transaction verification before confirmation
- Firebase indexing for fast queries

### ✅ Marketplace
- Browse all active domains (listed + unlisted)
- Filter and sort by price, date, length
- Fixed-price listings
- Instant purchase with automatic transfer
- 5% platform fee (stays in contract treasury)
- 95% goes to seller
- Real-time transaction history

### ✅ Referral Program  
- Unique referral codes for all users
- 10% commission on referred registrations
- 4-tier cashback system (Bronze → Platinum)
- Automatic earnings tracking in Firebase
- Dashboard with complete referral analytics
- Must own ≥1 domain to refer others

### ✅ User Dashboard
- Portfolio view of all owned domains
- Active marketplace listings management
- Referral statistics and earnings
- Transaction history with timestamps
- Domain management (transfer, list, delist)

### ✅ NFT Cards
- Dynamically generated visual cards
- Unique gradient backgrounds
- QR code for verification
- PNG format for maximum compatibility
- Hosted on IPFS via Pinata
- Accessible via `https://ipfs.io/ipfs/{cid}`

### ✅ Integration
- Endless Wallet authentication
- Endless blockchain RPC queries
- Firebase for user data and indexing
- IPFS for decentralized metadata storage
- Canvas-based server-side rendering

---

## Try It Out (Test on Testnet)

### Prerequisites
1. Install [Endless Wallet](https://wallet.endless.link/) browser extension
3. Connect to Endless Testnet in Endless Wallet

### Quick Start
```bash
# Visit the platform
https://luxury-banoffee-b4a82b.netlify.app/

# Search for a domain
# Connect your Endless wallet
# Register your first .eds domain
# Check your dashboard
# List it on marketplace (optional)
```

### Example User Journey
1. Search: "myname" → Available ✅
2. Price: 10 EDS (example)
3. Connect Endless → Approve transaction
4. Wait ~5 seconds for confirmation
5. Domain appears in dashboard
6. NFT visible in Endless wallet
7. Can now list it for sale or transfer it

---

## For Developers

### Run Frontend Locally
```bash
git clone <repo>
cd EDS-Name
npm install
npm run dev
# Open http://localhost:5173
```

### Run Backend Locally  
```bash
cd EDS-Name-backend
npm install

# Set environment variables
cp .env.example .env
# Add your Firebase, Pinata, Endless RPC credentials

npm run build
npm start
# API runs on http://localhost:3001
```

### Deploy Smart Contracts
```bash
cd move/eds_name
endless move compile
endless move publish --network testnet
# Copy deployed address to config
```

### Environment Variables Required

**Backend (.env)**
```bash
FIREBASE_PROJECT_ID=your-project
FIREBASE_PRIVATE_KEY=your-key
PINATA_JWT=your-pinata-jwt
ENDLESS_RPC_URL=https://fullnode.testnet.endless.network/v1
CONTRACT_ADDRESS=0x... (your deployed contract)
CONTRACT_PRIVATE_KEY=your-contract-key
BACKEND_URL=http://localhost:3001
```

**Frontend (.env)**
```bash
VITE_API_URL=http://localhost:3001
VITE_ENDLESS_NETWORK=testnet
VITE_MODULE_ADDRESS=0x... (your contract)
```

---

## Architecture Deep Dive

### API Endpoints

**Domains**
```
POST /domains/pre-register
  → Generates metadata & uploads to IPFS
  → Returns metadataUri and cardSvgUrl
  
POST /domains/register  
  → Verifies on-chain transaction
  → Saves domain to Firebase
  → Processes referral commission

GET /domains/search/:name
  → Checks availability
  → Returns registration info if exists

GET /domains/owner/:address
  → Returns all domains owned by address
```

**Marketplace**
```
GET /marketplace/browse
  → Returns all listed + minted domains
  → Sorted by price/date

POST /marketplace/list
  → Creates new listing
  
POST /marketplace/buy
  → Verifies payment transaction
  → Transfers ownership on-chain
  → Pays out seller (95%) + fee (5%)
  
POST /marketplace/cancel
  → Removes listing
```

**Referrals**
```
GET /referrals/:address
  → Returns referral stats
  → Total referrals, earnings, tier

POST /referrals/withdraw
  → Sends accumulated earnings to user
  → Uses contract wallet to pay out
```

**Stats**
```
GET /stats/global
  → Total domains registered
  → Total marketplace volume
  → Active users count
```

### Transaction Verification

Every transaction that transfers value is verified on-chain before being accepted:

```typescript
async function verifyPaymentTransaction(params: {
  txHash: string;
  expectedSender: string;
  expectedRecipient: string;
  minAmountEds: number;
}) {
  // 1. Fetch transaction from Endless RPC
  const tx = await endlessClient.getTransactionByHash(txHash);
  
  // 2. Verify sender matches
  if (tx.sender !== expectedSender) throw new Error('Sender mismatch');
  
  // 3. Verify recipient and amount in payload
  const transferEvent = tx.events.find(e => 
    e.type === '0x1::endless_account::TransferEvent'
  );
  
  if (transferEvent.data.to !== expectedRecipient) 
    throw new Error('Recipient mismatch');
    
  if (transferEvent.data.amount < minAmountEds) 
    throw new Error('Insufficient amount');
  
  // 4. Only accept successful transactions
  if (!tx.success) throw new Error('Transaction failed');
  
  return true;
}
```

This prevents:
- Fake transaction hashes
- Transactions to wrong addresses
- Insufficient payment amounts
- Failed transactions being counted

---

## Security & Safety

### What We've Implemented
✅ On-chain transaction verification before accepting registrations  
✅ Firebase security rules (users can only write to their own data)  
✅ Rate limiting on API endpoints  
✅ Input validation using Zod schemas  
✅ CORS restricted to frontend domain  
✅ Contract wallet for automated payouts (referrals, marketplace)  

---

## Contributing

We welcome contributions! Here's how you can help:

### Areas We Need Help With
- **Frontend:** UI/UX improvements, new features, bug fixes
- **Backend:** API optimizations, caching, performance
- **Smart Contracts:** Security audits, gas optimizations
- **Documentation:** Tutorials, guides, translations
- **Testing:** Writing tests, finding bugs

### How to Contribute
1. Fork the repo
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Test thoroughly
5. Submit a PR with clear description

### Code Style
- TypeScript for all new code
- Use ESLint + Prettier (configs included)
- Write descriptive commit messages
- Add comments for complex logic

---

## Community & Support

### Get Help
- **Twitter:** [@EDSName](https://x.com/EDSNameService) (coming soon)
- **Email:** ??

### Report Issues
Found a bug? Have a feature request?
- Open an issue on GitHub
- Tag with appropriate label (bug, enhancement, question)
- Provide reproduction steps if possible

### Stay Updated
- Follow our Twitter for announcements
- Join Discord for real-time discussions
- Check GitHub releases for updates

---

## FAQ

**Q: Do domains expire?**  
A: No. Once registered, your .eds domain is yours forever (or until you transfer/sell it).

**Q: Can I transfer my domain to another wallet?**  
A: Yes. Either sell it on the marketplace or transfer it directly through Endless wallet.

**Q: How do referrals work?**  
A: You need to own at least 1 domain first. Then share your wallet address as a referral code. When someone registers using your code, you earn 10% of their registration price.

**Q: What happens to marketplace fees?**  
A: 5% stays in the contract treasury (for future platform development). 95% goes to the seller.

**Q: Can I list my domain for any price?**  
A: Yes. Set any price you want. The market will decide if it's fair.

**Q: What if someone already owns the name I want?**  
A: Check if it's listed on the marketplace. If not, you could try contacting the owner (future feature).

**Q: Is the platform decentralized?**  
A: The smart contracts are fully decentralized on Endless blockchain. The backend API is currently centralized for performance but indexes all data from on-chain events.

**Q: Can I use my .eds name right now?**  
A: The naming resolution is live. Future integrations with wallets, dApps, and explorers will make it universally usable.

---

## License

MIT License - see LICENSE file for details.

---

## Acknowledgments

Built with ❤️ by the .EDS Name team

**Remember: Web3 should be simple. Your identity should be memorable. That's why we built .EDS Name.**

🌐 **Register your domain today:** https://luxury-banoffee-b4a82b.netlify.app/

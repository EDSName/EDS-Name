# 🌐 .EDS Name

### **The Future of Digital Identity on the Blockchain**

*Transforming complex addresses into memorable human names*

• [🚀 Live Demo ](https://luxury-banoffee-b4a82b.netlify.app/) 
• [📚 Documentation ](https://luxury-banoffee-b4a82b.netlify.app/docs)

</div>

## 🎯 What is .EDS Name?

**.EDS Name** is a revolutionary **Naming Service** platform built on the Endless blockchain, which allows users to transform complex cryptographic addresses into readable and memorable names.

Imagine replacing `0x742d35Cc6634C0532925a3b844Bc9e7595f0bEb` with simply `alice.eds` — **that's exactly what we do!**

### 💡 Why is .EDS Name Different?

- **🔗 Native Blockchain Integration**: Smart contracts developed in Move Language running natively on the Endless Blockchain.
- **🎨 Domain NFTs**: Each domain is a unique, negotiable NFT that is entirely yours.
- **💰 Integrated Marketplace**: Buy, sell, and auction domains with ease.
- **🎁 Referral System**: Earn rewards by referring new users.
- **🔒 Cutting-Edge Security**: Web3 Authentication with Petra Wallet and decentralized architecture

## ✨ Main Features

### 🎨 **NFT Domain Name System**
- Registration of unique and exclusive `.eds` domains
- Each domain is minted as NFT in the Endless standard
- Ownership transfer and trading

### 🏪 **Decentralized Marketplace**
- **Domain Listing**: Put your domains up for sale
- **Direct Offers**: Make offers on unlisted domains
- **Transaction History**: Complete on-chain tracking

### 👥 **Advanced Referral Program**
- Earn **10% commission** on every referred record

### 📊 **Professional Dashboard**
- **Domain Management**: View and manage all your .eds
- **Real-Time Analytics**: Usage, sales, and referral statistics
- **Complete History**: All recorded transactions and events

## 🏗️ Architecture

### 📐 Technology Stack

#### **Frontend** (React + TypeScript)
```
├── ⚛️ React 18 + Vite
├── 🎨 Tailwind CSS + Shadcn/ui
├── 🔄 Zustand (State Management)
├── 🛣️ React Router v7
├── 🎭 Framer Motion (Animations)
├── 📊 Recharts (Graphics)
└── 🔗 Aptos SDK (Blockchain Integration)
```

#### **Backend** (Node.js + TypeScript)
```
├── 🚂 Express.js
├── 🔥 Firebase (Database & Auth)
├── 📦 Pinata (IPFS Storage)
├── 🎴 Canvas (NFT Card Generation)
└── ⛓️ Endless SDK (Blockchain)
```

#### **Blockchain** (Move Language)
```
├── 📝 Smart Contracts in Move
├── 🏛️ Endless Framework
├── 🔐 Object-Based Architecture
└── 📜 Domain Registry Module
```

### 🎯 Smart Contract Architecture

The main contract `domain_registry.move` implements:

- **Object System**: Utilizes Endless's object system for decentralized management
- **Event-Driven**: Emits events for all critical operations
- **Extensible**: Supports custom metadata via IPFS
- **Secure**: Strict validations and owner-based access control

```move
module endless_addr::domain_registry {
    struct DomainRegistry has key {
        // Gestão de domínios
        domains: Table<String, address>,
        // Sistema de expiração
        expiration_dates: Table<String, u64>,
        // Metadados IPFS
        ipfs_hashes: Table<String, String>
    }
}
```

---

## 🚀 Funcionalidades Técnicas Avançadas

### 🎴 **Geração Dinâmica de NFT Cards**
Sistema de renderização server-side que gera cards visuais únicos para cada domínio:
- Metadados on-chain
- Upload automático para IPFS

### 🔄 **Sistema de Resolução**
Resolução bidirecional completa:
- **Forward**: `.eds` → `0x...` (endereço)
- **Reverse**: `0x...` → `.eds` (nome primário)
- **Multi-chain**: Suporte para diferentes redes

### 📈 **Analytics & Stats**
Dashboard com métricas em tempo real:
- Total de domínios registrados
- Volume de transações no marketplace
- Usuários ativos
- Receita gerada por referrals

### 🔔 **Notification System**
Smart notifications for:

- New offers received
- Completed sales
- Referral rewards credited
---

## 🔐 Security

### Implemented Practices
- ✅ **Web3 Authentication**: Only through Endless Wallet
- ✅ **Transaction Validation**: All operations validated on-chain
- ✅ **CORS Configured**: Only authorized origins
- ✅ **Rate Limiting**: Protection against API abuse
- ✅ **Input Sanitization**: Strict data validation
- ✅ **Encrypted Storage**: Sensitive data encrypted


## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

## 🏆 Team

Developed with ❤️ by a developer passionate about Web3 and blockchain.

## 📞 Contact and Support

- 🌐 **Website**: [eds-name.netlify.app](https://luxury-banoffee-b4a82b.netlify.app/)
- 🐦 **Twitter**: [@EDSName](https://twitter.com/edsname)

<div align="center">

### ⭐ If you liked the project, leave a star!

**Made with 💜 for the Web3 community**

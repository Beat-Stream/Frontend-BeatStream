# 🎵 BeatStream Frontend

This repository contains the **frontend application** for BeatStream.

The frontend provides a user-friendly interface where artists and listeners can interact with the BeatStream protocol.

---

# 🚀 Overview

Users can:

- Connect their wallet
- Upload and mint music NFTs
- Stream music
- Track royalty earnings
- View music ownership

The frontend communicates with both the **backend API** and the **Soroban smart contracts**.

---

# 🛠 Features

### Wallet Connection
Connect using Freighter Wallet.

### Music NFT Minting
Artists can upload music and mint NFTs.

### Music Streaming
Listeners can stream music through a pay-per-play model.

### Royalty Dashboard
Artists can track earnings and streaming activity.

---

# 🏗 Tech Stack

- Next.js
- React
- TailwindCSS
- Framer Motion
- Soroban Client
- Freighter Wallet

---

# 📂 Project Structure


frontend
│
├── src
│ ├── components
│ ├── pages
│ ├── hooks
│ └── utils
│
├── public
└── styles


---

# ⚙️ Installation

Install dependencies:


npm install


---

# 🚦 Run Development Server


npm run dev


Visit:


http://localhost:3000


---

# 🔗 Backend Connection

Configure the backend API URL in `.env`:


NEXT_PUBLIC_API_URL=http://localhost:5000


---

# 🔐 Wallet Integration

BeatStream uses **Freighter Wallet** for:

- Signing transactions
- Minting NFTs
- Receiving royalty payments

---

# 📄 License

MIT License
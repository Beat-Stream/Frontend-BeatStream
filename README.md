# 🎵 BeatStream Frontend

A modern, decentralized music streaming platform built on Stellar's Soroban smart contracts. This frontend application provides artists and listeners with an intuitive interface to mint music NFTs, stream content, and manage royalty payments in a transparent, blockchain-powered ecosystem.

---

## Table of Contents
- [🎯 Overview](#-overview)
- [✨ Features](#-features)
- [🏛 Architecture](#-architecture)
- [🛠 Tech Stack](#-tech-stack)
- [🚀 Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Development](#development)
- [📂 Project Structure](#-project-structure)
- [🔗 Smart Contracts](#-smart-contracts)
- [💻 Frontend Application](#-frontend-application)
- [🧪 Testing](#-testing)
- [🚢 Deployment](#-deployment)
- [⚙️ Configuration](#-configuration)
- [📡 API Reference](#-api-reference)
- [🤝 Contributing](#-contributing)
- [🗺 Roadmap](#-roadmap)
- [❓ FAQ](#-faq)
- [📄 License](#-license)
- [💬 Support](#-support)

---

## 🎯 Overview

BeatStream Frontend is the user-facing application for the BeatStream decentralized music platform. Built with Next.js and React, it provides a seamless Web3 experience for:

- **Artists**: Upload music, mint NFTs, track royalties, and manage their catalog
- **Listeners**: Discover music, stream tracks via pay-per-play, and support artists directly
- **Collectors**: Purchase music NFTs and build digital music collections

The application integrates with Stellar's Soroban smart contracts for on-chain operations and communicates with a backend API for off-chain data management, metadata storage, and media streaming.


## ✨ Features

### 🔐 Wallet Connection
- Seamless integration with **Freighter Wallet** for Stellar network
- Secure transaction signing and account management
- Support for testnet and mainnet environments
- Automatic wallet detection and connection status

### 🎨 Music NFT Minting
- Intuitive upload interface for audio files (MP3, WAV, FLAC)
- Metadata editor for track information (title, artist, genre, cover art)
- Real-time minting progress with transaction confirmation
- Automatic IPFS upload for decentralized storage
- NFT preview before minting

### 🎵 Music Streaming
- High-quality audio player with standard controls
- Pay-per-play model with transparent pricing
- Playlist creation and management
- Search and discovery features
- Genre-based filtering and recommendations

### 💰 Royalty Dashboard
- Real-time earnings tracking for artists
- Detailed analytics on streams, plays, and revenue
- Historical data visualization with charts
- Withdrawal functionality for accumulated royalties
- Transaction history and audit trail

### 👤 User Profiles
- Customizable artist and listener profiles
- Music library management
- Collection showcase for owned NFTs
- Social features and follower system

### 🎨 Modern UI/UX
- Responsive design for mobile, tablet, and desktop
- Dark/light theme support
- Smooth animations with Framer Motion
- Accessible components following WCAG guidelines
- Loading states and error handling


## 🏛 Architecture

The BeatStream frontend follows a modern, component-based architecture:

```
┌─────────────────────────────────────────────────────────────┐
│                     BeatStream Frontend                      │
│                      (Next.js + React)                       │
└────────────┬────────────────────────────────┬───────────────┘
             │                                │
             │                                │
    ┌────────▼────────┐              ┌───────▼────────┐
    │  Soroban Smart  │              │   Backend API   │
    │   Contracts     │              │   (REST/WS)     │
    │  (On-chain)     │              │  (Off-chain)    │
    └────────┬────────┘              └───────┬────────┘
             │                                │
             │                                │
    ┌────────▼────────┐              ┌───────▼────────┐
    │ Stellar Network │              │  IPFS Storage   │
    │   (Testnet/     │              │   (Metadata &   │
    │    Mainnet)     │              │     Media)      │
    └─────────────────┘              └─────────────────┘
```

### Key Components:

1. **Presentation Layer**: React components with TailwindCSS styling
2. **State Management**: React Context API and custom hooks
3. **Blockchain Integration**: Soroban SDK for smart contract interactions
4. **API Layer**: Axios-based HTTP client for backend communication
5. **Wallet Integration**: Freighter Wallet SDK for transaction signing
6. **Media Handling**: Custom audio player with streaming capabilities


## 🛠 Tech Stack

### Core Framework
- **Next.js 14+** - React framework with App Router, SSR, and API routes
- **React 18+** - UI library with hooks and concurrent features
- **TypeScript** - Type-safe development

### Styling & UI
- **TailwindCSS** - Utility-first CSS framework
- **Framer Motion** - Animation library for smooth transitions
- **Radix UI** - Accessible component primitives
- **Lucide Icons** - Modern icon library

### Blockchain & Web3
- **Soroban SDK** - Stellar smart contract interaction
- **Freighter Wallet SDK** - Wallet connection and signing
- **stellar-sdk** - Stellar network operations

### State & Data Management
- **React Context API** - Global state management
- **SWR / React Query** - Data fetching and caching
- **Zustand** - Lightweight state management (optional)

### Media & File Handling
- **Howler.js** - Audio playback library
- **IPFS HTTP Client** - Decentralized file storage
- **React Dropzone** - File upload interface

### Development Tools
- **ESLint** - Code linting
- **Prettier** - Code formatting
- **Husky** - Git hooks
- **Jest & React Testing Library** - Unit and integration testing
- **Playwright** - End-to-end testing

### Build & Deployment
- **Vercel** - Hosting and deployment platform
- **Docker** - Containerization (optional)
- **GitHub Actions** - CI/CD pipeline


## 🚀 Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v18.0.0 or higher)
- **npm** (v9.0.0 or higher) or **yarn** (v1.22.0 or higher)
- **Git** for version control
- **Freighter Wallet** browser extension ([Install here](https://www.freighter.app/))

Optional but recommended:
- **VS Code** with ESLint and Prettier extensions
- **Docker** (for containerized development)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-org/beatstream-frontend.git
   cd beatstream-frontend
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Set up environment variables**
   
   Create a `.env.local` file in the root directory:
   ```bash
   cp .env.example .env.local
   ```

   Configure the following variables:
   ```env
   # API Configuration
   NEXT_PUBLIC_API_URL=http://localhost:5000
   NEXT_PUBLIC_WS_URL=ws://localhost:5000

   # Stellar Network
   NEXT_PUBLIC_STELLAR_NETWORK=testnet
   NEXT_PUBLIC_HORIZON_URL=https://horizon-testnet.stellar.org

   # Smart Contract Addresses
   NEXT_PUBLIC_NFT_CONTRACT_ID=your_nft_contract_id
   NEXT_PUBLIC_ROYALTY_CONTRACT_ID=your_royalty_contract_id
   NEXT_PUBLIC_STREAMING_CONTRACT_ID=your_streaming_contract_id

   # IPFS Configuration
   NEXT_PUBLIC_IPFS_GATEWAY=https://ipfs.io/ipfs/
   NEXT_PUBLIC_IPFS_API_URL=https://api.pinata.cloud

   # Feature Flags
   NEXT_PUBLIC_ENABLE_ANALYTICS=true
   NEXT_PUBLIC_ENABLE_NOTIFICATIONS=true
   ```

4. **Verify installation**
   ```bash
   npm run lint
   npm run type-check
   ```

### Development

1. **Start the development server**
   ```bash
   npm run dev
   ```

   The application will be available at `http://localhost:3000`

2. **Build for production**
   ```bash
   npm run build
   ```

3. **Start production server**
   ```bash
   npm start
   ```

4. **Run linting**
   ```bash
   npm run lint
   npm run lint:fix  # Auto-fix issues
   ```

5. **Format code**
   ```bash
   npm run format
   ```


## 📂 Project Structure

```
beatstream-frontend/
│
├── public/                      # Static assets
│   ├── images/                  # Image files
│   ├── fonts/                   # Custom fonts
│   └── favicon.ico              # Favicon
│
├── src/
│   ├── app/                     # Next.js App Router
│   │   ├── layout.tsx           # Root layout
│   │   ├── page.tsx             # Home page
│   │   ├── dashboard/           # Dashboard pages
│   │   ├── upload/              # Upload pages
│   │   ├── stream/              # Streaming pages
│   │   └── profile/             # Profile pages
│   │
│   ├── components/              # React components
│   │   ├── ui/                  # Reusable UI components
│   │   │   ├── Button.tsx
│   │   │   ├── Card.tsx
│   │   │   ├── Modal.tsx
│   │   │   └── Input.tsx
│   │   ├── layout/              # Layout components
│   │   │   ├── Header.tsx
│   │   │   ├── Footer.tsx
│   │   │   └── Sidebar.tsx
│   │   ├── music/               # Music-specific components
│   │   │   ├── AudioPlayer.tsx
│   │   │   ├── TrackCard.tsx
│   │   │   ├── Playlist.tsx
│   │   │   └── UploadForm.tsx
│   │   └── wallet/              # Wallet components
│   │       ├── ConnectButton.tsx
│   │       └── WalletInfo.tsx
│   │
│   ├── hooks/                   # Custom React hooks
│   │   ├── useWallet.ts         # Wallet connection hook
│   │   ├── useContract.ts       # Smart contract interaction
│   │   ├── useAudio.ts          # Audio player hook
│   │   ├── useRoyalties.ts      # Royalty tracking hook
│   │   └── useIPFS.ts           # IPFS upload hook
│   │
│   ├── lib/                     # Utility libraries
│   │   ├── soroban/             # Soroban SDK utilities
│   │   │   ├── client.ts        # Contract client setup
│   │   │   ├── nft.ts           # NFT contract functions
│   │   │   ├── royalty.ts       # Royalty contract functions
│   │   │   └── streaming.ts     # Streaming contract functions
│   │   ├── api/                 # API client
│   │   │   ├── client.ts        # Axios instance
│   │   │   ├── music.ts         # Music endpoints
│   │   │   ├── user.ts          # User endpoints
│   │   │   └── analytics.ts     # Analytics endpoints
│   │   └── utils/               # Helper functions
│   │       ├── format.ts        # Formatting utilities
│   │       ├── validation.ts    # Input validation
│   │       └── constants.ts     # App constants
│   │
│   ├── context/                 # React Context providers
│   │   ├── WalletContext.tsx    # Wallet state
│   │   ├── AudioContext.tsx     # Audio player state
│   │   └── ThemeContext.tsx     # Theme state
│   │
│   ├── types/                   # TypeScript type definitions
│   │   ├── music.ts             # Music-related types
│   │   ├── user.ts              # User types
│   │   ├── contract.ts          # Contract types
│   │   └── api.ts               # API response types
│   │
│   └── styles/                  # Global styles
│       ├── globals.css          # Global CSS
│       └── themes.css           # Theme variables
│
├── tests/                       # Test files
│   ├── unit/                    # Unit tests
│   ├── integration/             # Integration tests
│   └── e2e/                     # End-to-end tests
│
├── .env.example                 # Environment variables template
├── .eslintrc.json               # ESLint configuration
├── .prettierrc                  # Prettier configuration
├── next.config.js               # Next.js configuration
├── tailwind.config.js           # Tailwind configuration
├── tsconfig.json                # TypeScript configuration
└── package.json                 # Dependencies and scripts
```


## 🔗 Smart Contracts

The frontend interacts with three main Soroban smart contracts deployed on the Stellar network:

### NFT Contract
Handles music NFT creation and ownership.

**Key Functions:**
- `mint_nft(artist, metadata_uri, royalty_percentage)` - Mint new music NFT
- `transfer_nft(token_id, from, to)` - Transfer NFT ownership
- `get_nft_info(token_id)` - Retrieve NFT metadata
- `get_owner(token_id)` - Get current NFT owner

### Royalty Contract
Manages royalty distribution and payments.

**Key Functions:**
- `distribute_royalty(token_id, amount)` - Distribute streaming revenue
- `claim_royalties(artist)` - Withdraw accumulated royalties
- `get_royalty_balance(artist)` - Check pending royalties
- `get_royalty_history(token_id)` - View payment history

### Streaming Contract
Handles pay-per-play streaming logic.

**Key Functions:**
- `initiate_stream(token_id, listener)` - Start a paid stream
- `record_play(token_id, listener)` - Record a completed play
- `get_stream_count(token_id)` - Get total plays
- `get_stream_price(token_id)` - Get current streaming price

### Contract Integration

The frontend uses the Soroban SDK to interact with these contracts:

```typescript
// Example: Minting an NFT
import { mintNFT } from '@/lib/soroban/nft';

const result = await mintNFT({
  artist: walletAddress,
  metadataUri: ipfsHash,
  royaltyPercentage: 10
});
```

All contract addresses are configured in environment variables and can be updated for different networks (testnet/mainnet).


## 💻 Frontend Application

### Key Pages & Routes

#### Home (`/`)
- Landing page with featured music
- Search and discovery interface
- Genre categories and trending tracks

#### Dashboard (`/dashboard`)
- Artist analytics and earnings overview
- Recent activity feed
- Quick actions (upload, view royalties)

#### Upload (`/upload`)
- Multi-step upload wizard
- Audio file upload with drag-and-drop
- Metadata form (title, artist, genre, cover art)
- Minting confirmation and transaction status

#### Stream (`/stream`)
- Music player interface
- Playlist management
- Queue and history

#### Profile (`/profile/[address]`)
- User profile information
- Music library (uploaded or owned)
- Follower/following lists
- Transaction history

#### Royalties (`/royalties`)
- Earnings dashboard with charts
- Detailed breakdown by track
- Withdrawal interface
- Payment history

### Component Architecture

#### Reusable UI Components
All UI components are built with accessibility and reusability in mind:

```typescript
// Example: Button component
<Button 
  variant="primary" 
  size="lg" 
  onClick={handleClick}
  disabled={isLoading}
>
  Connect Wallet
</Button>
```

#### Custom Hooks
Encapsulate complex logic for easy reuse:

```typescript
// Example: useWallet hook
const { 
  address, 
  isConnected, 
  connect, 
  disconnect, 
  signTransaction 
} = useWallet();
```

### State Management

The application uses React Context API for global state:

- **WalletContext**: Wallet connection status and user address
- **AudioContext**: Current playing track and player controls
- **ThemeContext**: Dark/light mode preferences

### API Integration

All backend API calls are centralized in the `lib/api` directory:

```typescript
// Example: Fetching user's music library
import { getUserTracks } from '@/lib/api/music';

const tracks = await getUserTracks(userAddress);
```


## 🧪 Testing

### Running Tests

```bash
# Run all tests
npm test

# Run unit tests
npm run test:unit

# Run integration tests
npm run test:integration

# Run e2e tests
npm run test:e2e

# Run tests in watch mode
npm run test:watch

# Generate coverage report
npm run test:coverage
```

### Test Structure

#### Unit Tests
Located in `tests/unit/`, these test individual components and functions:

```typescript
// Example: Button component test
describe('Button', () => {
  it('renders with correct text', () => {
    render(<Button>Click me</Button>);
    expect(screen.getByText('Click me')).toBeInTheDocument();
  });

  it('calls onClick handler when clicked', () => {
    const handleClick = jest.fn();
    render(<Button onClick={handleClick}>Click</Button>);
    fireEvent.click(screen.getByText('Click'));
    expect(handleClick).toHaveBeenCalledTimes(1);
  });
});
```

#### Integration Tests
Test interactions between multiple components and API calls:

```typescript
// Example: Upload flow test
describe('Music Upload Flow', () => {
  it('uploads and mints NFT successfully', async () => {
    // Test complete upload workflow
  });
});
```

#### E2E Tests
Full user journey tests using Playwright:

```typescript
// Example: E2E test
test('user can connect wallet and upload music', async ({ page }) => {
  await page.goto('/');
  await page.click('text=Connect Wallet');
  // ... rest of the test
});
```

### Testing Best Practices

- Mock external dependencies (wallet, contracts, API)
- Use data-testid attributes for reliable selectors
- Test user interactions, not implementation details
- Maintain >80% code coverage
- Run tests in CI/CD pipeline


## 🚢 Deployment

### Vercel Deployment (Recommended)

1. **Connect your repository to Vercel**
   - Visit [vercel.com](https://vercel.com)
   - Import your GitHub repository
   - Vercel will auto-detect Next.js

2. **Configure environment variables**
   - Add all variables from `.env.local` in Vercel dashboard
   - Set production contract addresses
   - Configure production API URLs

3. **Deploy**
   ```bash
   # Automatic deployment on git push
   git push origin main
   
   # Or use Vercel CLI
   npm install -g vercel
   vercel --prod
   ```

### Docker Deployment

1. **Build Docker image**
   ```bash
   docker build -t beatstream-frontend .
   ```

2. **Run container**
   ```bash
   docker run -p 3000:3000 \
     -e NEXT_PUBLIC_API_URL=https://api.beatstream.io \
     beatstream-frontend
   ```

3. **Docker Compose**
   ```yaml
   version: '3.8'
   services:
     frontend:
       build: .
       ports:
         - "3000:3000"
       env_file:
         - .env.production
   ```

### Manual Deployment

1. **Build the application**
   ```bash
   npm run build
   ```

2. **Start the production server**
   ```bash
   npm start
   ```

3. **Use a process manager (PM2)**
   ```bash
   npm install -g pm2
   pm2 start npm --name "beatstream-frontend" -- start
   pm2 save
   pm2 startup
   ```

### CI/CD Pipeline

GitHub Actions workflow example (`.github/workflows/deploy.yml`):

```yaml
name: Deploy to Production

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm ci
      - run: npm run lint
      - run: npm run test
      - run: npm run build
      - uses: amondnet/vercel-action@v20
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.ORG_ID }}
          vercel-project-id: ${{ secrets.PROJECT_ID }}
```

### Environment-Specific Configurations

- **Development**: `.env.local` with testnet contracts
- **Staging**: `.env.staging` with staging API and testnet
- **Production**: `.env.production` with mainnet contracts and production API


## ⚙️ Configuration

### Environment Variables

| Variable | Description | Required | Default |
|----------|-------------|----------|---------|
| `NEXT_PUBLIC_API_URL` | Backend API base URL | Yes | - |
| `NEXT_PUBLIC_WS_URL` | WebSocket server URL | Yes | - |
| `NEXT_PUBLIC_STELLAR_NETWORK` | Stellar network (testnet/mainnet) | Yes | testnet |
| `NEXT_PUBLIC_HORIZON_URL` | Horizon server URL | Yes | - |
| `NEXT_PUBLIC_NFT_CONTRACT_ID` | NFT contract address | Yes | - |
| `NEXT_PUBLIC_ROYALTY_CONTRACT_ID` | Royalty contract address | Yes | - |
| `NEXT_PUBLIC_STREAMING_CONTRACT_ID` | Streaming contract address | Yes | - |
| `NEXT_PUBLIC_IPFS_GATEWAY` | IPFS gateway URL | Yes | - |
| `NEXT_PUBLIC_IPFS_API_URL` | IPFS API endpoint | No | - |
| `NEXT_PUBLIC_ENABLE_ANALYTICS` | Enable analytics tracking | No | false |
| `NEXT_PUBLIC_ENABLE_NOTIFICATIONS` | Enable push notifications | No | false |

### Next.js Configuration

Key settings in `next.config.js`:

```javascript
module.exports = {
  reactStrictMode: true,
  images: {
    domains: ['ipfs.io', 'gateway.pinata.cloud'],
  },
  webpack: (config) => {
    config.resolve.fallback = {
      fs: false,
      net: false,
      tls: false,
    };
    return config;
  },
};
```

### Tailwind Configuration

Customize theme in `tailwind.config.js`:

```javascript
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: '#6366f1',
        secondary: '#8b5cf6',
      },
      fontFamily: {
        sans: ['Inter', 'sans-serif'],
      },
    },
  },
};
```

### TypeScript Configuration

Strict mode enabled in `tsconfig.json`:

```json
{
  "compilerOptions": {
    "strict": true,
    "noUncheckedIndexedAccess": true,
    "noImplicitReturns": true
  }
}
```


## 📡 API Reference

### Backend API Endpoints

The frontend communicates with the following backend endpoints:

#### Music Endpoints

```typescript
// Get all tracks
GET /api/music/tracks
Response: Track[]

// Get track by ID
GET /api/music/tracks/:id
Response: Track

// Upload track metadata
POST /api/music/upload
Body: { title, artist, genre, coverArt, audioFile }
Response: { trackId, ipfsHash }

// Search tracks
GET /api/music/search?q=query
Response: Track[]
```

#### User Endpoints

```typescript
// Get user profile
GET /api/users/:address
Response: UserProfile

// Update user profile
PUT /api/users/:address
Body: { name, bio, avatar }
Response: UserProfile

// Get user's tracks
GET /api/users/:address/tracks
Response: Track[]
```

#### Royalty Endpoints

```typescript
// Get royalty balance
GET /api/royalties/:address
Response: { balance, pending, claimed }

// Get royalty history
GET /api/royalties/:address/history
Response: RoyaltyTransaction[]

// Get track earnings
GET /api/royalties/track/:tokenId
Response: { totalEarnings, streamCount }
```

#### Analytics Endpoints

```typescript
// Get track analytics
GET /api/analytics/track/:tokenId
Response: { plays, revenue, listeners }

// Get artist analytics
GET /api/analytics/artist/:address
Response: { totalPlays, totalRevenue, topTracks }
```

### WebSocket Events

Real-time updates via WebSocket:

```typescript
// Connect to WebSocket
const ws = new WebSocket(NEXT_PUBLIC_WS_URL);

// Listen for events
ws.on('stream:started', (data) => {
  // Handle stream start
});

ws.on('royalty:received', (data) => {
  // Handle royalty payment
});

ws.on('nft:minted', (data) => {
  // Handle new NFT
});
```

### Contract Interaction Examples

```typescript
// Mint NFT
import { mintNFT } from '@/lib/soroban/nft';

const tx = await mintNFT({
  artist: walletAddress,
  metadataUri: 'ipfs://...',
  royaltyPercentage: 10
});

// Claim royalties
import { claimRoyalties } from '@/lib/soroban/royalty';

const tx = await claimRoyalties(walletAddress);

// Initiate stream
import { initiateStream } from '@/lib/soroban/streaming';

const tx = await initiateStream({
  tokenId: '123',
  listener: walletAddress
});
```


## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

### Getting Started

1. **Fork the repository**
   ```bash
   # Click the 'Fork' button on GitHub
   ```

2. **Clone your fork**
   ```bash
   git clone https://github.com/your-username/beatstream-frontend.git
   cd beatstream-frontend
   ```

3. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

4. **Make your changes**
   - Write clean, documented code
   - Follow the existing code style
   - Add tests for new features
   - Update documentation as needed

5. **Commit your changes**
   ```bash
   git add .
   git commit -m "feat: add your feature description"
   ```

   Follow [Conventional Commits](https://www.conventionalcommits.org/):
   - `feat:` New feature
   - `fix:` Bug fix
   - `docs:` Documentation changes
   - `style:` Code style changes (formatting)
   - `refactor:` Code refactoring
   - `test:` Adding or updating tests
   - `chore:` Maintenance tasks

6. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```

7. **Open a Pull Request**
   - Go to the original repository
   - Click "New Pull Request"
   - Provide a clear description of your changes

### Development Guidelines

- Write TypeScript with strict type checking
- Use functional components with hooks
- Follow the existing project structure
- Ensure all tests pass before submitting
- Keep components small and focused
- Use meaningful variable and function names
- Add comments for complex logic
- Ensure accessibility compliance

### Code Review Process

1. Automated checks must pass (linting, tests, build)
2. At least one maintainer review required
3. Address all review comments
4. Squash commits before merging

### Reporting Issues

Found a bug? Have a feature request?

1. Check existing issues first
2. Use issue templates
3. Provide detailed reproduction steps
4. Include screenshots/videos if applicable
5. Specify your environment (browser, OS, wallet version)

### Community Guidelines

- Be respectful and inclusive
- Help others learn and grow
- Provide constructive feedback
- Follow our [Code of Conduct](CODE_OF_CONDUCT.md)


## 🗺 Roadmap

### Phase 1: Core Features (Q1 2026) ✅
- [x] Wallet integration with Freighter
- [x] Basic music upload and minting
- [x] Audio player with streaming
- [x] Royalty dashboard
- [x] User profiles

### Phase 2: Enhanced Features (Q2 2026) 🚧
- [ ] Advanced search and filtering
- [ ] Playlist creation and sharing
- [ ] Social features (follow, like, comment)
- [ ] Mobile-responsive design improvements
- [ ] Dark/light theme toggle
- [ ] Multi-language support (i18n)

### Phase 3: Advanced Features (Q3 2026) 📋
- [ ] NFT marketplace integration
- [ ] Collaborative playlists
- [ ] Artist verification system
- [ ] Advanced analytics dashboard
- [ ] Push notifications
- [ ] Offline mode with PWA

### Phase 4: Ecosystem Growth (Q4 2026) 🔮
- [ ] Mobile app (React Native)
- [ ] Desktop app (Electron)
- [ ] Integration with other Stellar dApps
- [ ] DAO governance features
- [ ] Advanced royalty splitting
- [ ] Live streaming capabilities

### Future Considerations
- AI-powered music recommendations
- Virtual concert experiences
- Cross-chain bridge support
- Music NFT fractionalization
- Decentralized content moderation

### Community Requests
Have a feature idea? [Open an issue](https://github.com/your-org/beatstream-frontend/issues) with the `feature-request` label!


## ❓ FAQ

### General Questions

**Q: What is BeatStream?**  
A: BeatStream is a decentralized music streaming platform built on Stellar's Soroban smart contracts. It allows artists to mint music NFTs, earn royalties transparently, and gives listeners a pay-per-play streaming experience.

**Q: Do I need cryptocurrency to use BeatStream?**  
A: Yes, you need XLM (Stellar Lumens) to pay for transactions like minting NFTs and streaming music. You'll also need the Freighter Wallet browser extension.

**Q: Is BeatStream free to use?**  
A: Creating an account and browsing music is free. However, minting NFTs and streaming music require small transaction fees paid in XLM.

### Technical Questions

**Q: Which browsers are supported?**  
A: BeatStream works best on Chrome, Firefox, Brave, and Edge. Safari support is experimental. You must have the Freighter Wallet extension installed.

**Q: What audio formats are supported?**  
A: We support MP3, WAV, and FLAC files. Maximum file size is 50MB per track.

**Q: Where is my music stored?**  
A: Audio files and metadata are stored on IPFS (InterPlanetary File System) for decentralized, permanent storage. Only ownership records and transaction data are stored on the Stellar blockchain.

**Q: Can I use BeatStream on mobile?**  
A: The web app is mobile-responsive, but wallet functionality may be limited. Native mobile apps are planned for Q4 2026.

### Wallet & Transactions

**Q: How do I get XLM for transactions?**  
A: You can purchase XLM on exchanges like Coinbase, Kraken, or Binance, then transfer it to your Freighter Wallet.

**Q: What are the transaction fees?**  
A: Stellar transaction fees are minimal (typically 0.00001 XLM). Streaming costs are set by artists, usually 0.01-0.1 XLM per play.

**Q: How long do transactions take?**  
A: Stellar transactions typically confirm in 3-5 seconds.

**Q: Can I use a different wallet?**  
A: Currently, only Freighter Wallet is supported. Additional wallet support is planned for future releases.

### Artist Questions

**Q: How do royalties work?**  
A: When listeners stream your music, payments are automatically distributed via smart contracts. You can claim accumulated royalties anytime from your dashboard.

**Q: What percentage of streaming revenue do artists keep?**  
A: Artists keep 90% of streaming revenue. 10% goes to platform maintenance and development.

**Q: Can I update my music after minting?**  
A: NFT metadata is immutable once minted. However, you can mint new versions and deprecate old ones.

**Q: How do I verify my artist profile?**  
A: Artist verification is coming in Phase 3. Join our Discord for updates.

### Troubleshooting

**Q: My wallet won't connect. What should I do?**  
A: Ensure Freighter Wallet is installed and unlocked. Try refreshing the page or reconnecting. Check that you're on the correct network (testnet/mainnet).

**Q: My transaction failed. Why?**  
A: Common reasons include insufficient XLM balance, network congestion, or incorrect contract addresses. Check your wallet balance and try again.

**Q: The audio player isn't working.**  
A: Ensure your browser allows audio playback. Check your internet connection. Try a different browser if issues persist.

**Q: I found a bug. How do I report it?**  
A: Please [open an issue](https://github.com/your-org/beatstream-frontend/issues) on GitHub with detailed reproduction steps.


## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### MIT License Summary

```
Copyright (c) 2026 BeatStream

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

### Third-Party Licenses

This project uses open-source libraries. See [THIRD_PARTY_LICENSES.md](THIRD_PARTY_LICENSES.md) for details.

---


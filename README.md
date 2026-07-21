<div align="center">
  <img src="https://raw.githubusercontent.com/Sandeep6135/NetShield-Extention/main/public/Logo.png" alt="NetShield Logo" width="120" />

  # 🛡️ NetShield
  **A production-grade, privacy-first Manifest V3 extension for strict network-level website blocking.**

  [![Built with React](https://img.shields.io/badge/Built_with-React-61DAFB?style=for-the-badge&logo=react&logoColor=black)](#)
  [![Manifest V3](https://img.shields.io/badge/Chrome-Manifest_V3-4285F4?style=for-the-badge&logo=google-chrome&logoColor=white)](#)
  [![Vite](https://img.shields.io/badge/Bundled_by-Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)](#)
  [![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](#)
  [![Zustand](https://img.shields.io/badge/Zustand-764ABC?style=for-the-badge&logo=redux&logoColor=white)](#)
</div>

---

<br />

## 📖 Project Overview

**NetShield** is a highly optimized browser extension designed to intercept and drop network requests for distractive or restricted domains. Unlike traditional blockers that rely on content scripts or DOM manipulation, NetShield operates entirely at the browser's network layer using Chrome's declarative APIs.

This ensures zero-latency blocking, meaning restricted sites are dropped before a single byte of HTML is rendered. The extension is heavily protected by a robust cryptographic passkey system, preventing unauthorized deactivation or circumvention.

<br />

## 🛠️ Technology Stack

NetShield is built on a modern, highly performant web stack engineered for extension environments:

- **Core Engine**: Chrome Manifest V3 (`chrome.declarativeNetRequest`, `chrome.storage`)
- **Frontend Framework**: React 18
- **State Management**: Zustand (Synchronized with `chrome.storage.sync` & `local`)
- **Styling**: Tailwind CSS & PostCSS
- **Language**: Strict TypeScript
- **Bundler**: Vite (via `@crxjs/vite-plugin`)

<br />

## 🏗️ Architecture & Design Patterns

The architecture draws inspiration from industry-leading extensions (like Ghostery), strictly adhering to an event-driven, decoupled design pattern:

### 1. The Background Engine (`serviceWorker.ts`)
Operating as a Manifest V3 Service Worker, the background script remains entirely dormant until invoked by specific hardware/browser events. It avoids heavy polling loops and memory leaks.
- **Dynamic Rule Generation**: Listens to `chrome.storage.onChanged` and asynchronously computes and applies `declarativeNetRequest` rule matrices.
- **Stateless Operation**: Retains zero local memory state, pulling the source of truth directly from `chrome.storage` during execution cycles.

### 2. The Presentation Layer (`App.tsx` & Zustand)
The React popup operates as a "dumb" presentation layer. It does not calculate blocking logic or manage extension state.
- **Storage Proxies**: The Zustand store acts as a reactive proxy over `chrome.storage`, dispatching configuration updates which the background worker subsequently acts upon.

### 3. Cryptographic Security (`crypto.ts`)
- **Passkey Hashing**: Master passkeys are immediately digested via `crypto.subtle.digest` (SHA-256). The plaintext passkey is never stored in memory or storage, preventing extraction via DevTools memory dumps.

<br />

## 🚀 Installation & Setup

### Prerequisites
- [Node.js](https://nodejs.org/) (v18.0.0 or higher)
- [npm](https://npmjs.com/) 

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/Sandeep6135/NetShield-Extention.git
   cd NetShield-Extention
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Start the development server (HMR enabled)**
   ```bash
   npm run dev
   ```

4. **Build for production**
   ```bash
   npm run build
   ```

### Loading into Chrome
1. Navigate to `chrome://extensions/` in your browser.
2. Enable **Developer mode** using the toggle switch in the top right.
3. Click the **Load unpacked** button.
4. Select the generated `dist` folder located in the project root.

<br />

## 📚 Usage Guide
- **Initialization**: Upon first launch, you will be prompted to create a Master Passkey.
- **Adding Domains**: Open the NetShield popup and enter the root domain (e.g., `youtube.com`) to instantly drop all incoming/outgoing traffic to that host.
- **Bypassing**: If a restricted domain must be accessed, input your Master Passkey to grant a temporary, heavily monitored bypass session (1–480 minutes). The background worker will automatically re-engage the block upon expiration.

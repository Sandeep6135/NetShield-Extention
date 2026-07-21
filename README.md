<div align="center">
  <img src="https://raw.githubusercontent.com/Sandeep6135/NetShield-Extention/main/public/Logo.png" alt="NetShield Logo" width="120" />

  # 🛡️ NetShield
  **A lightning-fast, zero-distraction website blocker I built to survive finals week.**

  [![Built with React](https://img.shields.io/badge/Built_with-React-61DAFB?style=for-the-badge&logo=react&logoColor=black)](#)
  [![Manifest V3](https://img.shields.io/badge/Chrome-Manifest_V3-4285F4?style=for-the-badge&logo=google-chrome&logoColor=white)](#)
  [![Vite](https://img.shields.io/badge/Bundled_by-Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)](#)
</div>

---

<br />

Hey! 👋 I built **NetShield** as a personal project because I needed a website blocker that was actually hard to bypass and didn't slow down my browser. It intercepts network requests at the browser level, meaning distracting sites drop dead before they even try to load. 

It's super lightweight, completely private, and heavily relies on Chrome's modern `declarativeNetRequest` API. 

## ✨ What makes it cool?

| Feature | Description |
| :--- | :--- |
| 🛑 **Instant Blocking** | Uses Chrome's native engine to kill network requests instantly. No page flashing, no loading. |
| 🔒 **Passkey Protected** | You set a master passkey when you install it. You can't turn off a block without it! |
| ⏳ **Temporary Bypasses** | Really need to check Twitter for a project? Grant yourself a strict 15-minute bypass. |
| 👻 **Ghost Mode** | The background service worker sleeps when you aren't actively changing rules, saving battery. |
| 🎨 **Clean UI** | A dark-mode first, minimalist popup built with React and Tailwind CSS. |

<br />

## 🛠️ The Tech Stack

I wanted to learn modern extension development, so I built this with some awesome tools:
- **Frontend**: React 18 & Tailwind CSS
- **State Management**: Zustand (synced with `chrome.storage`)
- **Core API**: Chrome Manifest V3
- **Build Tool**: Vite (it's so fast!)

<br />

## 🚀 How to try it out

Want to run this on your own machine? It's super simple.

1. **Clone the repo**
   ```bash
   git clone https://github.com/Sandeep6135/NetShield-Extention.git
   cd NetShield-Extention
   ```

2. **Install the dependencies**
   ```bash
   npm install
   ```

3. **Build the extension**
   ```bash
   npm run build
   ```

4. **Load it into Chrome**
   - Go to `chrome://extensions/` in your browser.
   - Toggle on **Developer mode** in the top right corner.
   - Click **Load unpacked** and select the `dist` folder inside the project.

<br />

## 💡 Why I built this
I was tired of complex blockers with subscriptions or weird permissions. I just wanted something that was built well, looked good, and helped me study. Feel free to use the code, learn from it, or modify it for your own needs!

<div align="center">
  <p><i>Made with ❤️ and too much coffee.</i></p>
</div>

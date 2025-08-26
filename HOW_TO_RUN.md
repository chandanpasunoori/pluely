# How to Run Pluely 🚀

This guide will help you get Pluely (The Open Source Alternative to Cluely) up and running on your local machine for development or to build it for production.

## 📋 Prerequisites

Before you begin, make sure you have the following installed:

### Required Software
- **Node.js** (v18 or higher) - [Download Node.js](https://nodejs.org/)
- **Rust** (latest stable) - [Install Rust](https://rustup.rs/)
- **npm** or **yarn** (npm comes with Node.js)

### System Dependencies

#### Linux (Ubuntu/Debian)
```bash
sudo apt update
sudo apt install -y libwebkit2gtk-4.1-dev build-essential curl wget libssl-dev libgtk-3-dev libayatana-appindicator3-dev librsvg2-dev pkg-config
```

#### macOS
```bash
# Install Xcode command line tools if not already installed
xcode-select --install
```

#### Windows
- Install **Microsoft C++ Build Tools** or **Visual Studio** with C++ support
- Install **WebView2** (usually comes with Windows 11 or newer versions of Windows 10)

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/chandanpasunoori/pluely.git
cd pluely
```

### 2. Install Dependencies
```bash
npm install
```

### 3. Start Development Server
```bash
npm run tauri dev
```

This command will:
- Build the frontend using Vite
- Compile the Rust backend
- Launch the Pluely desktop application
- Enable hot reload for development

**Note:** The first run will take several minutes (2-5 minutes) as it compiles all Rust dependencies. Subsequent runs will be much faster.

## 🛠️ Development Commands

### Start Development Server
```bash
npm run tauri dev
```
Starts the application in development mode with hot reload.

### Build for Production
```bash
# Build the frontend
npm run build

# Build the entire application
npm run tauri build
```

This creates platform-specific installers in `src-tauri/target/release/bundle/`:
- **macOS**: `.dmg` file
- **Windows**: `.msi` installer  
- **Linux**: `.deb` file

### Preview Production Build
```bash
npm run preview
```
Preview the production build locally.

### Frontend Only (Web Mode)
```bash
npm run dev
```
Runs only the frontend at `http://localhost:1420/` for web development.

## ⚙️ Configuration

### AI Provider Setup
1. Launch the application
2. Go to Settings
3. Select your preferred AI provider (OpenAI, Claude, Gemini, Grok, etc.)
4. Enter your API key
5. Select or enter your preferred model

### Speech-to-Text Setup
1. In Settings, go to STT Providers
2. Select your preferred speech-to-text provider
3. Configure the API credentials
4. Test the voice input functionality

## 🐛 Troubleshooting

### Common Issues and Solutions

#### Issue: "Failed to initialize GTK backend" on Linux
**Solution:** Install the required GTK dependencies:
```bash
sudo apt install -y libwebkit2gtk-4.1-dev libgtk-3-dev
```

#### Issue: Build fails with "glib-2.0 not found"
**Solution:** Install pkg-config and glib development packages:
```bash
sudo apt install -y pkg-config libglib2.0-dev
```

#### Issue: "error while running tauri application" on Windows
**Solution:** 
1. Install Microsoft C++ Build Tools
2. Install WebView2 Runtime
3. Restart your terminal/IDE

#### Issue: Node.js version conflicts
**Solution:** Use Node.js v18 or higher:
```bash
# Check your Node.js version
node --version

# If you need to upgrade, use nvm (Node Version Manager)
nvm install 18
nvm use 18
```

#### Issue: Rust not found
**Solution:** Install Rust using rustup:
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source ~/.cargo/env
```

#### Issue: Permission denied on Linux
**Solution:** You might need to install additional libraries:
```bash
sudo apt install -y libappindicator3-dev libasound2-dev
```

## 📱 Platform-Specific Notes

### macOS
- On first run, you may need to grant permissions in System Preferences
- For screen capture features, enable Screen Recording permissions

### Linux
- The application requires X11 or Wayland display server
- Some distributions might need additional audio libraries for voice features

### Windows  
- Windows Defender might flag the application on first run (this is normal for unsigned applications)
- WebView2 is required and usually comes with Windows 10/11

## 🔧 Advanced Development

### Custom Build Configuration
You can modify build settings in:
- `src-tauri/tauri.conf.json` - Tauri configuration
- `src-tauri/Cargo.toml` - Rust dependencies
- `package.json` - Node.js dependencies and scripts

### Debug Mode
For detailed debugging:
```bash
RUST_BACKTRACE=1 npm run tauri dev
```

### Clean Build
If you encounter caching issues:
```bash
# Clean npm cache
npm clean-install

# Clean Rust build cache
cd src-tauri
cargo clean
cd ..

# Rebuild
npm run tauri dev
```

## 📚 Additional Resources

- [Tauri Documentation](https://tauri.app/v1/guides/)
- [Vite Documentation](https://vitejs.dev/guide/)
- [React Documentation](https://react.dev/)
- [Rust Documentation](https://doc.rust-lang.org/)

## 🆘 Getting Help

If you encounter issues not covered in this guide:

1. Check the [GitHub Issues](https://github.com/chandanpasunoori/pluely/issues)
2. Create a new issue with:
   - Your operating system and version
   - Node.js and Rust versions
   - Complete error message
   - Steps to reproduce the issue

---

## 🎯 What You'll See

Once running successfully, Pluely will launch as a desktop application with:
- A clean, minimal interface
- AI chat functionality
- Voice input capabilities (if configured)
- Settings panel for customization
- Always-on-top overlay mode

The application is designed to be lightweight (~10MB) and fast, providing an open-source alternative to commercial AI assistants.

---

**Happy coding!** 🚀

If you find this project helpful, consider starring the repository or contributing to its development.
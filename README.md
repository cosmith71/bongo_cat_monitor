# 🐱 Bongo Cat ESP32 - Your Cute Digital Typing Companion

![Bongo Cat](web%20resources/cat1.png)

Bongo Cat is a cute digital pet that lives on your desk and types along with you! This ESP32-based project displays a charming cat that responds to your typing speed, shows system statistics (CPU, RAM, WPM), and features adorable animations that bring joy to your workspace.

## ✨ Features

- **Real-time Typing Detection** - Cat types faster when you type faster
- **System Monitoring** - Displays CPU usage, RAM usage, and current time
- **WPM Tracking** - Shows your words per minute in real-time
- **Multiple Animations** - Various cute expressions and movements
- **Sleep Mode** - Cat goes to sleep when you're not active
- **Customizable Settings** - Adjust display preferences and behavior
- **Open Source** - Complete source code available
- **Easy Assembly** - No soldering required, around $10 to build

## 🛒 Hardware Requirements

You'll need an **ESP32 board with 2.4 inch TFT display**. We used this board:

**[ESP32-2432S028R 2.4" TFT Display Board](https://www.aliexpress.com/item/1005008176009397.html?spm=a2g0o.order_list.order_list_main.4.5abc1802ZwAPQo)**

This board includes:
- ESP32-WROOM-32 module
- 2.4" ILI9341 TFT LCD (240x320 resolution)
- Touch screen capability
- USB-C connector
- All necessary components integrated

## 🚀 Quick Start

### Option 1: Web Flasher (Recommended)
1. **Flash the ESP32**: Visit our [Web Flasher](https://vostoklabs.github.io/Bongo_cat_webflasher/)
2. **Connect your ESP32** board with 2.4 inch TFT display to your computer's USB port
3. **Click "Connect"** and select your ESP32 device
4. **Click "Install"** and wait for the process to complete

### Option 2: Arduino IDE
1. Open `bongo_cat.ino` in Arduino IDE
2. Install required libraries (see Configuration section)
3. Select your ESP32 board and upload

### PC Application Setup
1. **Download** the PC application from `BongoCat_Release/BongoCat_Setup.exe`
2. **Install** and run the application
3. The app will **automatically find and connect** to your ESP32 board
4. **Check system tray** - the app runs in the background
5. **Right-click tray icon** to access settings and configure display options

## 📁 Project Structure

```
├── 📁 animations/              # Animation sprite data
│   ├── 📁 body/               # Body movement animations
│   ├── 📁 faces/              # Facial expressions
│   ├── 📁 paws/               # Paw movement animations
│   ├── 📁 effects/            # Special effects (clicks, sleep)
│   ├── 📁 table/              # Table/background elements
│   └── 📄 Animation guidelines.md
├── 📁 bongo_cat_app/          # Desktop companion application
│   ├── 📄 main.py             # Application entry point
│   ├── 📄 engine.py           # Core logic and serial communication
│   ├── 📄 gui.py              # Settings GUI
│   ├── 📄 tray.py             # System tray functionality
│   ├── 📄 config.py           # Configuration management
│   └── 📄 requirements_app.txt
├── 📁 BongoCat_Release/       # Windows installer package
│   ├── 📄 BongoCat_Setup.exe  # Ready-to-install executable
│   ├── 📄 README.md           # Installation instructions
│   └── 📄 LICENSE.txt
├── 📁 web resources/          # Web flasher assets
│   ├── 🖼️ cat1.png, cat2.png   # High-quality cat images
│   ├── 🎞️ typing.gif          # Typing animation examples
│   ├── 🎞️ typing fast.gif     # Fast typing animation
│   ├── 🎞️ sleeping.gif        # Sleep mode animation
│   └── 📸 settings.png        # Screenshots for documentation
├── 📁 3d_printing/            # 3D printable case files (coming soon)
│   └── 📄 case.3mf            # 3MF format case file
├── 📄 bongo_cat.ino           # Main ESP32 firmware
├── 📄 animations_sprites.h    # Sprite data header
├── 📄 lv_conf.h              # LVGL configuration
├── 📄 User_Setup.h           # TFT_eSPI library configuration
├── 📄 Free_Fonts.h           # Font definitions
├── 📄 manifest.json          # Web flasher configuration
└── 📄 LICENSE.txt            # MIT License
```

## 🎨 Animation System

The Bongo Cat features a sophisticated animation system with multiple states:

### Animation Categories
- **Idle States**: Default cat expressions and subtle movements
- **Typing States**: Paw movements that match your typing speed
- **Sleep Mode**: Peaceful sleeping animations when inactive
- **Special Effects**: Click effects and transitions

### Animation Examples
| State | Speed | Description |
|-------|-------|-------------|
| ![Typing](web%20resources/typing.gif) | Normal | Regular typing animation |
| ![Fast Typing](web%20resources/typing%20fast.gif) | Fast | High-speed typing animation |
| ![Sleeping](web%20resources/sleeping.gif) | Idle | Sleep mode when inactive |

### Adding Custom Animations
1. Create your sprite data in the `animations/` folder
2. Update `animations_sprites.h` with new sprite definitions
3. Modify the animation logic in `bongo_cat.ino`

## ⚙️ Configuration

### TFT_eSPI Library Setup
The `User_Setup.h` file contains the display configuration for your specific ESP32 board:

```cpp
#define ESP32_2432S028R     // Enable this for the recommended board
#define TFT_MOSI 23
#define TFT_MISO 19
#define TFT_SCLK 18
#define TFT_CS   15
#define TFT_DC   2
#define TFT_RST  4
```

### LVGL Configuration
The `lv_conf.h` file configures the LVGL graphics library:
- Display resolution: 240x320 pixels
- Color depth: 16-bit
- Animation settings
- Memory allocation

### Required Arduino Libraries
- **TFT_eSPI** (configured with User_Setup.h)
- **LVGL** (version 8.x)
- **WiFi** (for time synchronization)

## 🔧 Development

### Building from Source
1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/bongo-cat-esp32.git
   ```

2. **ESP32 Firmware**
   - Open `bongo_cat.ino` in Arduino IDE
   - Ensure libraries are installed
   - Upload to your ESP32

3. **Desktop Application**
   ```bash
   cd bongo_cat_app
   pip install -r requirements_app.txt
   python main.py
   ```

### Creating Installers
- **Windows**: Use `installer.nsi` with NSIS
- **Executable**: Use `bongo_cat.spec` with PyInstaller

## 🎯 PC Application Features

### System Tray Integration
![Tray Screenshot](web%20resources/tray%20screenshot.png)

The application runs quietly in your system tray and provides:
- Automatic ESP32 detection and connection
- Real-time data transmission
- System resource monitoring

### Settings Configuration
![Settings](web%20resources/settings.png)

Customize your Bongo Cat experience:
- **Display Options**: Choose what information to show
- **Sleep Timer**: Set inactivity timeout
- **Animation Speed**: Adjust responsiveness
- **Connection Settings**: COM port configuration

## 🛠️ 3D Printing (Coming Soon)

We're working on custom case designs for your Bongo Cat:

- **Material**: PLA recommended
- **Supports**: Minimal supports needed
- **Print Time**: Approximately 2-3 hours
- **File Format**: .3mf files for easy printing

## 📡 Communication Protocol

The ESP32 and PC application communicate via USB serial at 115200 baud:

### Commands
- `CPU:XX` - CPU usage percentage
- `RAM:XX` - RAM usage percentage  
- `WPM:XX` - Words per minute
- `TIME:HH:MM` - Current time
- `ANIM:X` - Animation state change

## 🤝 Contributing

We welcome contributions! Here's how to help:

1. **Fork** the repository
2. **Create** a feature branch
3. **Make** your changes
4. **Test** thoroughly
5. **Submit** a pull request

### Areas for Contribution
- New animations and sprites
- Additional display layouts
- Case designs and 3D models
- Code optimizations
- Documentation improvements

## 📝 License

This project is licensed under the MIT License - see the [LICENSE.txt](LICENSE.txt) file for details.

## 🙏 Acknowledgments

- Original Bongo Cat meme creators
- ESP32 and Arduino communities
- LVGL graphics library developers
- All contributors and supporters

## 📞 Support

- **Issues**: Report bugs on GitHub Issues
- **Discussions**: Join our community discussions
- **Web Flasher**: [https://vostoklabs.github.io/Bongo_cat_webflasher/](https://vostoklabs.github.io/Bongo_cat_webflasher/)

---

**Made with ❤️ for the love of cute cats and coding** 
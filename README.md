<div align="center">
  <img src="https://img.shields.io/badge/Version-4.3.2-blue?style=for-the-badge&logo=arduino" />
  <img src="https://img.shields.io/badge/Chip-ESP8266_D1_Mini-black?style=for-the-badge&logo=espressif" />
  <img src="https://img.shields.io/badge/Status-TRIAL-orange?style=for-the-badge" />
  <br><br>
  <img src="https://img.shields.io/badge/🛡️_Educational_Purpose_Only-IMPORTANT-red" />
</div>

<h1 align="center">⚡ AETHERNET TRIAL (ESP8266)</h1>
<p align="center">
  <b>Advanced WiFi Security Audit Tool & Game Launcher</b><br>
  <i>Compact single-module design featuring dual-firmware switching, physical button navigation, and an integrated web dashboard.</i>
</p>

<hr>

<h2>🎯 Feature Details</h2>

<h3>📡 WiFi Attacks (2.4GHz)</h3>
<ul>
  <li><b>Smart Deauth Attack:</b> Selectively disconnects targets using native ESP8266 packets, forcing devices to automatically connect to our fake network (Evil Twin).</li>
  <li><b>Evil Twin & Captive Portal:</b> 100% identical network cloning (Including SSID & Hidden SSID sniffer). Supports Custom HTML for highly realistic phishing pages.</li>
  <li><b>Rogue AP:</b> Creates a standalone fake Access Point with built-in Google login pages to capture credentials.</li>
  <li><b>Beacon Spam:</b> Floods the area with hundreds of fake SSIDs (Default or Customizable up to 50 different names).</li>
  <li><b>Password Auto-Verify:</b> When a victim enters a password on the phishing page, it automatically verifies its correctness against the real router in real-time.</li>
  <li><b>Deauth All:</b> Broadcasts deauthentication frames to all nearby networks simultaneously.</li>
  <li><b>Session Hijack & Router Guard:</b> Sniffs connected stations, allows selective deauthentication of specific clients, and guards the target AP.</li>
  <li><b>WiFi Extender (NAPT):</b> Acts as a universal repeater for any target network.</li>
</ul>

<h3>🕹️ Dual-Firmware & Main Game</h3>
<ul>
  <li><b>OTA Firmware Switching:</b> Switch between AETHERNET firmware and a custom Game firmware directly from the Web UI without unplugging the device.</li>
  <li><b>Built-in Mini Games:</b> Upload <code>aethernet_game.bin</code> via File Manager to unlock built-in games (Flappy Bird, Pong, Sudoku, 1916 Shooter) directly on the OLED screen.</li>
</ul>

<h3>🖥️ Interface & Control</h3>
<ul>
  <li><b>4x Physical Control Buttons:</b> Full offline navigation using tactile buttons (UP, DOWN, OK/SELECT, BACK) directly on the OLED menu.</li>
  <li><b>Web File Manager:</b> Upload custom HTML templates, update firmware (.bin), and monitor real-time Flash storage capacity directly from the browser.</li>
  <li><b>Dark Web Dashboard:</b> Futuristic web interface, mobile-responsive, equipped with a color theme system and live clock sync.</li>
  <li><b>Custom OLED UI:</b> Minimalist 3x5 pixel font rendering showing real-time attack stats, progress bars, and system logs.</li>
</ul>

<hr>

<h2>🛠️ Hardware & Pinout Specifications</h2>
<p><b>⚠️ STRICT WARNING:</b> This firmware is hard-coded specifically for the <b>LOLIN (WEMOS) D1 Mini</b> pinout below. Ensure strict adherence to this wiring diagram.</p>

<h3>1. OLED Display (SSD1306 128x64 - I2C)</h3>
<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>OLED Pin</th>
    <th style="text-align: center;">ESP8266 Pin</th>
    <th>Notes</th>
  </tr>
  <tr><td>SDA</td><td style="text-align: center;"><b>D2 (GPIO 4)</b></td><td>Data Line</td></tr>
  <tr><td>SCL</td><td style="text-align: center;"><b>D1 (GPIO 5)</b></td><td>Clock Line</td></tr>
  <tr><td>VCC</td><td style="text-align: center;"><b>3.3V</b></td><td>DO NOT use 5V</td></tr>
  <tr><td>GND</td><td style="text-align: center;"><b>GND</b></td><td>Common Ground</td></tr>
</table>
<p><i>* I2C Address must be set to <b>0x3C</b>.</i></p>

<h3>2. Physical Navigation Buttons (Tactile Push Buttons)</h3>
<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>Button Function</th>
    <th style="text-align: center;">ESP8266 Pin</th>
    <th>Notes</th>
  </tr>
  <tr><td>UP / Menu Up</td><td style="text-align: center;"><b>D5 (GPIO 14)</b></td><td>Connect to GND when pressed</td></tr>
  <tr><td>DOWN / Menu Down</td><td style="text-align: center;"><b>D6 (GPIO 12)</b></td><td>Connect to GND when pressed</td></tr>
  <tr><td>OK / SELECT</td><td style="text-align: center;"><b>D7 (GPIO 13)</b></td><td>Connect to GND when pressed</td></tr>
  <tr><td>BACK / KEMBALI</td><td style="text-align: center;"><b>D3 (GPIO 0)</b></td><td>Connect to GND when pressed</td></tr>
  <tr><td>START / MAIN GAME</td><td style="text-align: center;"><b>D4 (GPIO 2)</b></td><td>Connect to GND when pressed</td></tr>
</table>
<p><i>* Internal <code>INPUT_PULLUP</code> is enabled. No external resistors required. Just connect the button pins to the respective ESP8266 pins and GND.</i></p>

<hr>

<h2>📦 How to Flash the Firmware</h2>
<p>Since you are downloading the pre-compiled <code>.bin</code> file, you do not need the Arduino IDE. Follow these steps using the official ESP Flashing Tool:</p>

<h3>1. Preparation</h3>
<ul>
  <li>Install the USB Serial Driver for your D1 Mini (usually CH340 or CP2102) on your PC.</li>
  <li>Download and open the <b>ESP8266 Flash Download Tool</b> (from Espressif's official website).</li>
</ul>

<h3>2. Flashing Process</h3>
<ul>
  <li>Connect your ESP8266 D1 Mini to your PC via USB.</li>
  <li>Open the Flash Download Tool, select <b>Developer Mode</b> -> <b>ESP8266 DownloadTool</b>.</li>
  <li>Select the correct COM Port (check Device Manager if unsure) and set the Baudrate to <b>115200</b>.</li>
  <li>Check the first SPI Flashbox, click the <b>...</b> button and load the downloaded <b>AETHERNET.bin</code></b> file. Set the address to <b>0x00000</b>.</li>
  <li>Set the Flash Size to <b>32Mbit (4MB)</b>.</li>
  <li>Make sure <b>DoNotChgBin</b> is selected.</li>
  <li>Click <b>ERASE</b> first to wipe the board completely. Wait for it to finish.</li>
  <li>Click <b>START</b> to flash the firmware and wait for the green checkmark.</li>
  <li>Unplug and replug your ESP8266. The <b>ATHERNET SSID</b> will appear shortly.</li>
</ul>

<h3>❓ What if the SSID does not appear?</h3>
<ol>
  <li>The ESP8266 is still on bootloader mode. Unplug then plug it back in.</li>
  <li>You did not erase the flash before flashing (must click ERASE first).</li>
  <li>Wrong COM Port selected or driver not installed properly.</li>
  <li>Hardware wiring issue (e.g., buttons short-circuiting to GND on boot).</li>
</ol>

<hr>

<div align="center">
  <h2>💎 Get the Full / Premium Version</h2>
  <p>The file available in this repository is a <b>Trial Version</b>, strictly limited to <b>10 Minute</b> of usage time for initial demonstration. Once the trial expires, the device is permanently locked and requires re-flashing.</p>
  <br>
  <a href="https://t.me/+6283141852690">
  <img src="https://img.shields.io/badge/Buy_Now-Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" />
  </a>
  <br><br>
  <i>Click the button above to chat directly with me on Telegram.</i>
</div>

<hr>

<h2>📸 Preview & Documentation</h2>
<p><b>Web Dashboard Interface:</b></p>
<p align="center">
<img src="https://raw.githubusercontent.com/AtherNet29/Esp8266-Deauther-2.4-Ghz-Jammer-Bluetooth/bfbd55d4c29e50327f5f40f2d37576ec45e14e55/Dashboard.jpg" width="250" alt="Dashboard Preview" />
</p>

<p><b>Module Wiring Diagram (ESP8266 D1 Mini):</b></p>
<p align="center">
  <img src="https://raw.githubusercontent.com/AtherNet29/Esp8266-Deauther-2.4-Ghz-Jammer-Bluetooth/d59d4c38fe027164d3bf796934cf08dfc058e29b/SKEMA%20DIAGRAM.jpg" width="800" alt="Wiring Diagram" />
</p>

<hr>

<div align="justify" style="background-color: #ffcccc; padding: 15px; border-left: 5px solid #ff0000;">
  <h3>⚖️ Legal Disclaimer</h3>
  <b>STRICT WARNING:</b> This tool is created purely for <i>Penetration Testing</i> and <i>Educational Purposes</i> within the scope of network security. It is strictly forbidden to use this tool to attack, steal data, or disrupt networks that are NOT your property. Any form of abuse that violates your country's laws is <b>NOT</b> the responsibility of the Developer. By using this firmware, you agree to these terms and conditions.
</div>

<div align="center">
  <br>
  <sub>Built with ❤️ by AETHERNET Developer Team</sub>
</div>

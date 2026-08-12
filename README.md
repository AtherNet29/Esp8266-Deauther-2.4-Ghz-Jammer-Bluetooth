<div align="center">
  <img src="https://img.shields.io/badge/Version-4.3.2-blue?style=for-the-badge&logo=arduino" />
  <img src="https://img.shields.io/badge/Chip-ESP8266_D1_Mini-black?style=for-the-badge&logo=espressif" />
  <img src="https://img.shields.io/badge/Status-TRIAL-orange?style=for-the-badge" />
  <br><br>
  <img src="https://img.shields.io/badge/🛡️_Educational_Purpose_Only-IMPORTANT-red" />
</div>

<h1 align="center">⚡ AETHERNET PRO (ESP8266)</h1>
<p align="center">
  <b>Advanced WiFi & Bluetooth Security Audit Tool</b><br>
  <i>Compact single-module design to stress-test the resilience of 2.4GHz WiFi and Bluetooth networks.</i>
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
  <li><b>Router Guard:</b> Protects a specific AP by continuously deauthing unwanted connected clients.</li>
  <li><b>WiFi Extender:</b> Acts as a universal repeater for any target network with NAPT support.</li>
</ul>

<h3>📻 Bluetooth Attacks</h3>
<ul>
  <li><b>BT Jammer (JAMBLUE):</b> Uses 1x NRF24L01 to perform Continuous Wave Sweeping on BT frequencies, testing the vulnerability of Bluetooth IoT devices.</li>
</ul>

<h3>🖥️ Interface & Control</h3>
<ul>
  <li><b>Dark Web Dashboard:</b> Futuristic web interface, mobile-responsive, equipped with a color theme system and live clock sync.</li>
  <li><b>Custom OLED UI:</b> Minimalist 3x5 pixel font rendering showing real-time attack stats, progress bars, and system logs.</li>
  <li><b>Template Manager:</b> Upload, preview, and set active HTML phishing templates directly from the browser.</li>
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

<h3>2. NRF24L01 - Bluetooth Jammer (Hardware SPI)</h3>
<table border="1" style="border-collapse: collapse; width: 100%; text-align: left; padding: 8px;">
  <tr style="background-color: #f2f2f2;">
    <th>NRF24L01 Pin</th>
    <th style="text-align: center;">ESP8266 Pin</th>
    <th>Notes</th>
  </tr>
  <tr><td>CE</td><td style="text-align: center;"><b>D4 (GPIO 2)</b></td><td>Chip Enable</td></tr>
  <tr><td>CSN</td><td style="text-align: center;"><b>D0 (GPIO 16)</b></td><td>Chip Select</td></tr>
  <tr><td>SCK</td><td style="text-align: center;"><b>D5 (GPIO 14)</b></td><td>Hardware SPI CLK</td></tr>
  <tr><td>MOSI</td><td style="text-align: center;"><b>D7 (GPIO 13)</b></td><td>Hardware SPI MOSI</td></tr>
  <tr><td>MISO</td><td style="text-align: center;"><b>D6 (GPIO 12)</b></td><td>Hardware SPI MISO</td></tr>
  <tr><td>VCC</td><td style="text-align: center;"><b>3.3V</b></td><td>DO NOT use 5V</td></tr>
  <tr><td>GND</td><td style="text-align: center;"><b>GND</b></td><td>Common Ground</td></tr>
</table>
<p><b>⚠️ IMPORTANT:</b> Solder a <b>10uF Capacitor</b> directly between the VCC and GND pins on the NRF24L01 module to prevent voltage drops and crashes during transmission.</p>

<hr>

<h2>📦 How to Flash the Firmware</h2>

<h3>1. Flashing the ESP8266 (Wemos D1 Mini)</h3>
<ul>
  <li>Make sure you have installed USB Serial Driver (CH340/CP2102) on your PC.</li>
  <li>Open <b>Arduino IDE</b> or <b>ESP Flash Download Tool</b>.</li>
  <li>Select Board: <i>LOLIN(WEMOS) D1 Mini</i>.</li>
  <li>Erase the board flash first (Erase All Flash).</li>
  <li>Load the <b>.bin</b> file.</li>
  <li>Set the offset to <b>0x00000</b>.</li>
  <li>Click Flash and wait for the process to finish.</li>
  <li><b>ATHERNET SSID will appear shortly.</b></li>
</ul>

<h3>❓ What if the SSID does not appear?</h3>
<ol>
  <li>The ESP8266 is still on bootloader mode. Unplug then plug it back in.</li>
  <li>The binary file does not match with your ESP8266 Chip.</li>
  <li>You did not erase the flash before flashing.</li>
  <li>Hardware wiring issue (e.g., NRF24L01 short circuit blocking boot).</li>
</ol>

<hr>

<div align="center">
  <h2>💎 Get the Full / Premium Version</h2>
  <p>The file available in this repository is a <b>Trial Version</b>, strictly limited to <b>1 Minute</b> of usage time for initial demonstration. Once the trial expires, the device is permanently locked.</p>
  <p><b>Benefits of purchasing the Premium Version:</b></p>
  <p>
    ✅ No Time Limits (Premium Unlimited/Permanent).<br>
    ✅ Get Latest Updates (Can be upgraded to newer versions later).<br>
    ✅ Each purchase includes 2 free updates. You can request it anytime if there is a newer release.<br>
    Contact me on Telegram if you are interested.<br>
    The price above is for 1 copy of the binary file and cannot be duplicated.<br>
    ✅ Technical Support via Telegram (Troubleshooting and custom wiring assistance).
  </p>
  <h3>🛒 Price: RP 40.000</h3>
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
  <img src="https://raw.githubusercontent.com/AtherNet29/AtherNet-Esp32-Combo-Bw16-RTL8720DN/134ee7f6ee2d5a1805c25577202dfdea174c7670/HALAMAN%20DASHBOAR.jpg" width="800" alt="Dashboard Preview" />
</p>

<p><b>Module Wiring Diagram (ESP8266 D1 Mini):</b></p>
<p align="center">
  <img src="GAMBAR_SKEMATIK_ESP8266_ANDA_DISINI.jpg" width="800" alt="Wiring Diagram" />
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

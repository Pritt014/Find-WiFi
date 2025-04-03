# WiFi Network Scanner

## Overview
This script retrieves and displays available WiFi networks on both Windows and Linux.

## Prerequisites
- Windows or Linux operating system
- Python installed (version 3.x recommended)

## Installation
1. Clone this repository:
   ```sh
   git clone https://github.com/Pritt014/Find-WiFi.git
   cd Find-WiFi
   ```
2. Ensure Python is installed by running:
   ```sh
   python --version
   ```

## Usage
Run the script using:
```sh
python wifi_scanner.py
```

## Code Explanation
The script:
1. Detects the operating system (Windows or Linux).
2. Executes the appropriate command (`netsh` for Windows, `nmcli` for Linux) via Python’s `subprocess` module.
3. Captures the output and decodes it.
4. Prints the available WiFi networks.

## Code
```python
import subprocess
import platform

def scan_wifi():
    system_os = platform.system()

    if system_os == "Windows":
        command = ["netsh", "wlan", "show", "network"]
    elif system_os == "Linux":
        command = ["nmcli", "-t", "-f", "SSID", "dev", "wifi"]
    else:
        print("Unsupported OS")
        return

    try:
        output = subprocess.check_output(command, stderr=subprocess.DEVNULL)
        decoded_output = output.decode("utf-8")
        print(decoded_output)
    except Exception as e:
        print(f"Error scanning WiFi networks: {e}")

if __name__ == "__main__":
    scan_wifi()
```

## Notes
- Windows uses `netsh`, while Linux uses `nmcli`.
- Run the script in a command prompt or terminal with appropriate permissions.

## Repository Link
Find the project on GitHub: [Find-WiFi](https://github.com/Pritt014/Find-WiFi)

## License
This project is licensed under the MIT License.


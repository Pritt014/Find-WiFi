# WiFi Network Scanner

## Overview
This script retrieves and displays available WiFi networks on a Windows machine using the `netsh` command.

## Prerequisites
- Windows operating system
- Python installed (version 3.x recommended)

## Installation
1. Clone this repository:
   ```sh
   git clone https://github.com/yourusername/wifi-network-scanner.git
   cd wifi-network-scanner
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
1. Executes the `netsh wlan show network` command via Python’s `subprocess` module.
2. Captures the output and decodes it from ASCII.
3. Prints the available WiFi networks.

## Code
```python
import subprocess

nw = subprocess.check_output(['netsh', 'wlan', 'show', 'network'])
decoded_nw = nw.decode('ascii')
print(decoded_nw)
```

## Notes
- This script works only on Windows.
- Run the script in a command prompt with administrative privileges for best results.

## License
This project is licensed under the MIT License.


# Python Simple Port Scanner

## 📌 Introduction
This is a simple **Python-based Port Scanner** that scans a range of ports on a given target IP or domain to check for open ports. It uses **multi-threading** to speed up the scanning process and provides quick results.

## 🔥 Features
- ✅ **Uses Python's `socket` module** to check for open TCP ports.
- ✅ **Supports multi-threading** for faster scanning.
- ✅ **Command-line interface** to specify target and port range.
- ✅ **Error handling** for incorrect inputs and name resolution issues.
- ✅ **Execution time measurement** for performance tracking.

## 📜 How It Works
1. The script takes three command-line arguments:
   - `TARGET` (Domain name or IP address)
   - `START_PORT` (Starting port number)
   - `END_PORT` (Ending port number)
2. It converts the target hostname to an IP address.
3. It scans each port in the given range using **multi-threading**.
4. If a port is open, it displays the port number.
5. It measures and prints the total execution time.

## 🛠️ Requirements
- Python 3.x

## 🚀 Installation & Usage
### 1️⃣ Clone the Repository
```sh
git clone https://github.com/your-username/port-scanner.git
cd port-scanner
```

### 2️⃣ Run the Scanner
```sh
python3 Port_Scanner.py <TARGET> <START_PORT> <END_PORT>
```
**Example:**
```sh
python3 Port_Scanner.py google.com 20 100
```
## 📸 Sample Output
![Port Scanner Output](![WhatsApp Image 2025-03-04 at 22 08 20_b22119dc](https://github.com/user-attachments/assets/9cf43511-600f-4f65-81a8-51676031e26b)
)

## 📜 Code Explanation
```python
import socket
import sys
import time
import threading
```
- **`socket`**: Allows network communication.
- **`sys`**: Handles command-line arguments.
- **`time`**: Measures execution time.
- **`threading`**: Enables multi-threaded scanning for efficiency.

### Hostname Resolution
```python
try:
    target = socket.gethostbyname(sys.argv[1])
except socket.gaierror:
    print("Name resolution error")
    sys.exit()
```
- Converts hostname to an IP address.
- Handles invalid domains gracefully.

### Port Scanning Function
```python
def scan_port(port):
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    conn = s.connect_ex((target, port))
    s.settimeout(2)
    if (not conn):
        print("Port {} is OPEN".format(port))
    s.close()
```
- Creates a TCP socket.
- Attempts a connection using `connect_ex()`.
- If successful (`0` return value), prints open ports.
- Sets a **timeout** to avoid delays.

### Multi-threaded Scanning
```python
for port in range(start_port, end_port+1):
    thread = threading.Thread(target=scan_port, args=(port,))
    thread.start()
```
- Creates and starts a **new thread for each port**.
- Allows multiple ports to be scanned **simultaneously**.

## 📌 Potential Improvements
🔹 **Limit the Number of Threads** (Using `ThreadPoolExecutor` for better control)
🔹 **Better Output Formatting** (Sorting results, color-coded output)
🔹 **UDP Scanning Support** (Using `SOCK_DGRAM` instead of `SOCK_STREAM`)
🔹 **Handling Keyboard Interrupts** (Gracefully stopping on `CTRL+C`)

## 👨‍💻 Author
**Your Name** – [GitHub](https://github.com/avnisinngh) | [LinkedIn]([https://linkedin.com/in/avnidns](https://www.linkedin.com/in/avni-singh-49a44a289/))

## 📄 License
This project is licensed under the **MIT License**.

---
Feel free to contribute or suggest improvements! 🚀


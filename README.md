# 🔧 MAC Address Changer

A simple command-line tool for changing network interface MAC addresses. Uses ifconfig commands to modify MAC addresses with basic validation and error handling.


## ✨ Features

### 🔧 **Core Functionality**
- **MAC Address Changing**: Modify network interface MAC addresses
- **Interface Support**: Works with any network interface
- **Basic Validation**: MAC address format checking
- **Status Display**: Show current MAC before and after changes

### 🛠️ **Technical Features**
- **ifconfig Integration**: Uses system ifconfig commands
- **Subprocess Management**: Safe command execution
- **Regular Expression Parsing**: Extract MAC addresses from output
- **Error Handling**: Basic error checking and reporting

### 📊 **Output Information**
- **Current MAC Display**: Shows existing MAC address
- **Change Confirmation**: Displays new MAC after change
- **Status Messages**: Clear operation feedback
- **Error Reporting**: Informative error messages

## 🚀 Quick Start

### **Installation**
```bash
# No external dependencies required
# Uses only Python standard library modules

# Run the MAC changer
python macChanger.py
```

### **Basic Usage**
```bash
# Change MAC address for specific interface
python macChanger.py -i eth0 -m 00:11:22:33:44:55

# Example with wireless interface
python macChanger.py -i wlan0 -m 11:22:33:44:55:66
```

## 🎯 Command Line Options

| Option | Description | Example |
|--------|-------------|---------|
| `-i, --interface` | Network interface name | `-i eth0` |
| `-m, --mac` | New MAC address | `-m 00:11:22:33:44:55` |
| `-h, --help` | Show help message | `-h` |

### **Examples**

```bash
# Change MAC on Ethernet interface
python macChanger.py -i eth0 -m 00:11:22:33:44:55

# Change MAC on Wireless interface
python macChanger.py -i wlan0 -m 11:22:33:44:55:66

# Get help
python macChanger.py -h
```

## 📊 Output Format

### **Standard Output**
```
Current MAC = 00:11:22:33:44:55
[+] Changing MAC address for eth0 to 11:22:33:44:55:66
Current MAC = 11:22:33:44:55:66
```

### **Error Output**
```
[-] Please specify an interface, use --help for more info.
[-] Please specify a new mac, use --help for more info.
[-] Could not read MAC address.
```

## 🔧 How It Works

### **Process Flow**
1. **Parse Arguments**: Extract interface and MAC from command line
2. **Get Current MAC**: Read existing MAC address using ifconfig
3. **Bring Interface Down**: Disable network interface
4. **Change MAC**: Set new MAC address using ifconfig
5. **Bring Interface Up**: Re-enable network interface
6. **Verify Change**: Display new MAC address

### **Commands Used**
```bash
# Get current MAC
ifconfig <interface>

# Change MAC address
ifconfig <interface> down
ifconfig <interface> hw ether <new_mac>
ifconfig <interface> up
```

## ⚡ Usage Guidelines

### **MAC Address Format**
- **Standard Format**: `XX:XX:XX:XX:XX:XX`
- **Valid Characters**: Hexadecimal (0-9, A-F, a-f)
- **Length**: Exactly 12 characters (6 bytes)

### **Common Interfaces**
- **Linux**: `eth0`, `wlan0`, `ens33`
- **macOS**: `en0`, `en1`, `lo0`
- **Other**: Any valid network interface name

### **Privilege Requirements**
- **Linux/macOS**: May require `sudo` privileges
- **Windows**: May require Administrator rights
- **Network Access**: Interface must be accessible

## 🐛 Troubleshooting

### **Common Issues**

#### **"Permission denied"**
```bash
# Run with administrator privileges
sudo python macChanger.py -i eth0 -m 00:11:22:33:44:55

# On Windows, run as Administrator
python macChanger.py -i "Ethernet" -m 00:11:22:33:44:55
```

#### **"Interface not found"**
```bash
# Check available interfaces
ifconfig

# Use correct interface name
python macChanger.py -i wlan0 -m 00:11:22:33:44:55
```

#### **"Could not read MAC address"**
```bash
# Check interface status
ifconfig eth0

# Ensure interface is up
sudo ifconfig eth0 up
```

#### **"Invalid MAC address"**
```bash
# Use correct format
python macChanger.py -i eth0 -m 00:11:22:33:44:55

# Check MAC format
# Must be: XX:XX:XX:XX:XX:XX
```

### **Getting Help**
```bash
# Show help
python macChanger.py -h

# Check interface status
ifconfig

# Verify Python version
python --version
```

## 🔒 Security & Legal

### **Important Notes**
- **Only change MAC addresses on interfaces you own**
- **Some networks may block MAC changes**
- **Use responsibly and legally**
- **Backup original MAC addresses**

### **Best Practices**
- Test on your own network first
- Document original MAC addresses
- Use appropriate privileges
- Respect network policies

## 📁 File Structure

```
network-scanner/
├── macChanger.py           # MAC address changer
├── main.py                 # Network scanner
├── gui_scanner.py          # GUI scanner
├── requirements_macChanger.txt # Dependencies
└── README_macChanger.md    # This documentation
```

## 🛠️ Requirements

- **Python 3.6+**
- **Network interface access** (may require sudo/administrator)
- **ifconfig command** available on system

### **Dependencies**
```
# No external dependencies required
# Uses only Python standard library:
# - subprocess (for system commands)
# - optparse (for argument parsing)
# - re (for regular expressions)
```

## 🤝 Contributing

1. Create a feature branch
2. Make your changes
3. Test thoroughly
4. Submit your improvements

## 📄 License

This project is for educational purposes. Use responsibly and in accordance with local laws and network policies.

## 🙏 Acknowledgments

- **Python community**: Open source contributions
- **Network administrators**: Testing and feedback
- **ifconfig**: System command integration

---

**Happy MAC Changing!** 🔧

*Remember: Always use responsibly and only on interfaces you own or have permission to modify.* 

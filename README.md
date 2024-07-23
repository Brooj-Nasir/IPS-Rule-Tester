# Suricata IPS Rule Tester

This script tests network connectivity for various protocols (ICMP, HTTP, HTTPS, SSH) to determine if connections are being blocked by an Intrusion Prevention System (IPS). It provides diagnostic messages and generates custom Suricata rules if blockages are detected.

## Code Description:
The script contains a main function that provides a user interface for selecting the protocol to test. It uses the subprocess module to run system commands (ping, curl, ssh) and captures their output to determine if the connection is successful or blocked by the IPS.

## Functions
-**test_protocol(protocol, ip)**
This function tests the specified protocol against the given IP address and returns a tuple indicating if the connection is blocked and a diagnostic message.

### Parameters:

-**protocol (str)**: The protocol to test (icmp, http, https, ssh).
-**ip (str)**: The IP address to test against.

### Returns:

-**(bool, str)**: A tuple where the first element is True if the connection is blocked and False otherwise, and the second element is a diagnostic message.

## Features

- **ICMP Test:** Checks if ICMP packets can reach the target IP.
- **HTTP Test:** Verifies if an HTTP connection can be established to the target IP.
- **HTTPS Test:** Ensures HTTPS connectivity to the target IP.
- **SSH Test:** Tests the ability to connect to the target IP via SSH.
- **Custom Suricata Rules:** Generates Suricata rules to identify blockages.

## Prerequisites

- Python 3.x
- `termcolor` library: Install using `pip install termcolor`
- `curl` and `ping` commands available on your system
## Code File:

For whole code click here [ips-rule-tester](ips-rule-tester)

## Usage

### Running the Application

1. Navigate to the project directory.
   ```bash
   cd suricata-ips-tester
   ```
2. Run the script.

   ```bash
   python test_ips.py
   ```
3. Follow the on-screen instructions to select the protocol you wish to test:
   
![sel](https://github.com/user-attachments/assets/811a3856-7921-4741-aba4-e7ee4506d4b7) 


## Sample Code:
```python
...
if __name__ == "__main__":
    print("Welcome to Suricata IPS Rule Tester")

    ip = "192.168.240.129"
    while True:
        print("\nSelect a protocol to test:")
        print("1. ICMP")
        print("2. HTTP")
        print("3. HTTPS")
        print("4. SSH")
        print("5. Exit")

        choice = input("Enter your choice (1/2/3/4/5): ")

        if choice == '1':
            blocked, message = test_protocol('icmp', ip)
            if blocked:
                print(colored("----------------------------------------------------------", 'red'))
                print(colored("ICMP connection blocked by IPS. Reason:", 'red'))
                print(colored("----------------------------------------------------------", 'red'))
                print(colored(message, 'red'))
                print(colored("----------------------------------------------------------", 'red'))
            else:
                print(colored("----------------------------------------------------------", 'green'))
                print(colored("ICMP connection allowed.", 'green'))
                print(colored("----------------------------------------------------------", 'green'))
                print(colored(message, 'green'))
                print(colored
...
```

## Contributions:
No contributions are welcome without the permission of the author [Brooj-Nasir].

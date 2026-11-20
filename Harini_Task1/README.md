# OIBSIP â€“ Task 1: Basic Network Scanning with Nmap



## 1. Objective



To perform basic network scanning using Nmap in a local Kali Linux virtual machine, identify open ports and services, and analyse potential security risks.



## 2. Tools and Environment



- Nmap 7.99

- Kali Linux

- Oracle VirtualBox

- Python 3.13.12

- Windows host machine



## 3. Installation



Nmap was installed and verified in Kali Linux using:



```bash

nmap --version

```



## 4. Scanning Process



### Basic Localhost Scan



Command:



```bash

nmap 127.0.0.1

```



**Result:** Host was up. All 1000 commonly scanned TCP ports were closed.



### Local VM Network Address Scan



Command:



```bash

nmap 10.0.2.15

```



**Result:** Host was up. All 1000 scanned ports were filtered. No open ports were identified.



### Starting a Test HTTP Service



Command:



```bash

python3 -m http.server 8000 --bind 127.0.0.1

```



### Checking Listening Ports



Command:



```bash

ss -tuln

```



**Result:** TCP port 8000 was listening on 127.0.0.1.



### Service Version Detection



Command:



```bash

nmap -sV -p 8000 127.0.0.1

```



**Result:** Port 8000/tcp was open and identified as HTTP SimpleHTTPServer 0.6 (Python 3.13.12).



### Operating System Detection



Command:



```bash

sudo nmap -O -p 8000 127.0.0.1

```



**Result:** Linux OS guesses were displayed, but Nmap warned that the results might be unreliable because it could not find at least one open and one closed port. No exact OS match was confirmed.



## 5. Security Analysis



- **Closed ports:** No service was accepting connections on the scanned ports.

- **Filtered ports:** A firewall or network filtering may prevent Nmap from determining whether a port is open or closed.

- **Port 8000:** The Python HTTP development server was accessible through localhost only.

- **Security risk:** Development servers should not be exposed to untrusted networks. Files in the served directory may be accessible to clients that can connect to the server.

- **HTTP:** HTTP does not provide transport encryption.



## 6. Screenshots



The `screenshots` folder contains evidence of:



1. Nmap installation

2. Basic localhost scan

3. Local VM address scan

4. HTTP server running

5. Listening port 8000

6. Service version detection

7. OS detection



## 7. Conclusion



The task demonstrated basic network scanning, port identification, service version detection, and OS fingerprinting using Nmap. The tests were performed within the local Kali Linux environment. The results also demonstrated the difference between open, closed, and filtered ports.



## 8. Ethical Considerations



All scans were performed on the local machine or its local virtual environment. Network scanning should only be performed on systems for which permission has been granted.


# First step: Foundation of Networking, Linux, Cloud, and Security Awareness

## Preface

Since one of my bachelors is on software architecture, I have studied networking basics before, but Cloud/DevOps will be new. So with that in mind, this step will focus on refreshing my networking basics as well as learning the introduction to Cloud/DevOps


## 🎯 Goals

- Grasp the core principles of DevSecOps
- Learn networking fundamentals (OSI, ports, IP, firewalls)
- Become fluent with Linux command line tools
- Launch and secure your first EC2 instance on AWS
- Begin documentation on GitHub & Notion

## DevSecOps

To start delving into DevSecOps, first, I need to understand what DevOps in classical terms implies. The explanation from [AWS](https://aws.amazon.com/devops/what-is-devops/) website is more philosophical, so i'll lean more into the explanation from [Gitlab](https://about.gitlab.com/topics/devops/).

DevOps stands for development and operations. While these don't imply anything, the definition of the term itself is a practice or guidelines (methodology) that increase the efficiency, speed, and security of software development and delivery compared to traditional processes.

Now, the development part is self-explanatory, but how does the operations part play a role in DevOps?
While the development part is tied to software engineering, the operations part refers to the infrastructure, deployment, and maintenance side of the application lifecycle. The operations part also includes CI/CD (continuous integration / continuous delivery), which is a core component of DevOps.

DevOps is built upon four basic principles, which are:

1. Automation of the software development lifecycle.
2. Collaboration and communication.
3. Continuous improvement and minimization of waste.
4. Hyperfocus on user needs with short feedback loops.

That being said, how does the security part of DevSecOps come into play?

Taking info from [redhat](https://www.redhat.com/en/topics/devops/what-is-devsecops), security has mostly been a final stage process to add to the application development life cycle.
Since DevOps aims to have rapid and frequent development cycles, security must be integrated into the development process as well as security concerns can disrupt the DevOps practices.
The terms shift left and shift right security perfectly explain the mindset in integrating security into DevOps.

> To shift left is to incorporate security testing as soon as possible to find vulnerabilities and fix defects as early as possible in development.

> To shift right is to monitor user behavior, usage, performance, and security metrics in the production stage to verify software operability.

In summary, DevSecOps combines the practice of rapid development, continuous integration and delivery, secure and highly operable software development cycle

## Cybersecurity

The main topics to refresh for cybersecurity are the OSI Model, TCP/IP basics, ports, and firewalls.

The recommended video to watch is [Professor Meyer's Network Fundamentals](https://www.professormesser.com/network-plus/n10-006/network-fundamentals/).
The fundamental of the network is encapsulation and decapsulation. 
Encapsulation: The application data is first wrapped by a TCP header (Transmission Control Protocol), then an IP header (Internet Protocol), followed by the frame header and frame trailer.
Decapsulation is just the reverse of encapsulation.

Sending traffic across a network uses either a baseband network or a broadband network. 

#### Baseband Network

- Generally, a single cable with a digital signal, either copper or fiber.
- Communication signal uses all the bandwidth (either 100% or 0% utilization rate).
- Can be bidirectional, but not at the same time using the same wire or fiber.
- Ethernet standard
  - 100BASE-T, 1000BASE-T
    
#### Broadband Network

- Sending signals over different frequencies.
  - Multiple signals, multiple traffic types.
- Multiple simultaneous communication channels over the frequency spectrum
- Bidirectional communication in which sending uses one frequency and receiving uses another frequency.
- Internet, VOIP are examples.

#### Baud Rate vs Bit Rate

| Feature | Bit Rate | Baud Rate |
|---------|----------|-----------|
|What it measures |Number of bits transmitted per second|Number of signal changes per second|
|Units|bits per second (bps)|baud|
|Relationship|Can be equal to or greater than baud rate|Always less than or equal to bit rate|

Analogy, freight train.
Baud Rate: number of train carriages.
Bit Rate: number of passengers.

#### Wavelength

- A wavelength is the length where the sine wave is repeating.
- Higher frequencies have shorter wavelengths
  - A 2.4GHz has a wavelength of 12cm
  - Smaller wavelengths need smaller antennas
- Ethernet over fibers use a very small wavelength (we are talking about hundreds or thousandths of nm)

### [OSI Model](https://www.professormesser.com/network-plus/n10-006/understanding-the-osi-model/)

> Open Systems Interconnection Reference Model

It's a guide or guidelines, and not to be confused with OSI Protocol Suite. There are unique protocols at each layers.
The mnemonic to remember is that "all people seem need data processing."

| Layer 7: Application | Layer 6: Presentation | Layer 5: Transport | Layer 4: Session | Layer 3: Network | Layer 2: Data Link | Layer 1: Physical |
|---------|----------|-----------|---------|----------|-----------|-----------|

#### Layer 1: Physical

- The physics of the network
  - Signaling, cables, connectors.
  - Not about protocols.
- More on the hardware problem.

#### Layer 2: Data Link

- Data Link Control (DLC) Protocol
  - Media Access Control (MAC) address on Ethernet
- also referred to as the "switching" layer

#### Layer 3: Network

- The "Routing" layer
- IP (Internet Protocol)
- Fragment frames to traverse different networks

#### Layer 4: Session

- The "Post-office" layer
- Transmission Control Protocol (TCP) and User Datagram Protocol (UDP)

#### Layer 5: Transport

- Set up communication between devices
- It will start the communication flow, maintain the communication flow, and ultimately stop the communication flow between those devices.
- Also, set up a half duplex or full duplex connection between those devices.
- Might also include things like control protocols or tunneling protocols

#### Layer 6: Presentation

- Character encoding
- Application encryption and decryption (SSL/TSL)
- Often combined with layer 7 because of how closely they are integrated.

#### Layer 7: Application

- The layer we see

### Ports

> Port is a logical address of a 16-bit unsigned integer that is allotted to every application on the computer that uses the internet to send or receive data.

So, ports is basically the specific address on your machine that data is delivered to. Think of it as your house address and the mac address or ip address as the post office.
When we send parcel, it goes to the specific post office that is tasked for our area and then it delivers to your home address. Similarly, it is data to ip address to port.

There are three categories of port:
1. Well Known Port
2. Registered port
3. Dynamic Port

Well known port are reserved from 0 to 1023 and is usually tied to important services such as HTTP(port 80), FTP(port 21), DNS(Port 53), etc.

Registered port are reserved from 1024 to 49151 and are used by applications or services that are not as common.
But it is used by those applications or services which require its specific port.
Organizations can ask IANA(Internet Assigned Number Authority) for any specific port number within this range.

Dynamic port are reserved from 49152 to 65535
- It is also known as Ephemeral or Private Port
- It is used for those connections that are temporary or short-lived
- It is not registered or assigned and can be used by any process

### Firewall

> A firewall is a network security device either hardware or software-based which monitors all incoming and outgoing traffic and based on a defined set of security rules it accepts, rejects, or drops that specific
> traffic. It acts like a security guard that helps keep your digital world safe from unwanted visitors and potential threats.

- Accept: allow the traffic
- Reject: block the traffic but reply with an “unreachable error”
- Drop: block the traffic with no reply

A network traffic (whether incoming or outgoing) is matched against the rules or policies of the tables, and it will be accepted, rejected, or dropped depending state of the traffic itself.

There are a lot of types of firewalls, which I will be delving deeper into in the subsequent period of time if needed to.

# Wireshark-Packet-Capture

Completed a project using Wireshark to gain experience with capturing packets.

I used a Windows 10 VMware virtual machine to simulate the workstation. Firs thing's first, I installed instal ubuntu onto my workstation so I could use tools like tcpdump and Wireshark.
To ensure I installed the most update version of Wireshark, I use the command line, sudo add-apt-repository ppa:wireshark-dev/stable.
I then did sudo usermod -aG Wireshark $USER (of course, not actually USER but my own system --> ensured with the line whoami), to add myself to the wireshark group to add packet capture abilities.
Then, using Wireshark, I began the capturing packets and saved my results once the capturing had finished.

Here's where I began truly analyzing with Wireshark's filters. 
I used the command tcp.port==433 to identify any packets related to HTPPS traffic. By doing such, I found the command with the info "Client Hello", copied the desitination address, and input this address onto my web browser
Afterwards, I learned that rather than searching for these "Client Hello", "Server Hello", or "Certificate" messages when trying to access a website with the HTTPS protocol, I learned the command tls.handshake.type==1 to find these packets quicker.
These lines I anayzed were took place after the TCP handshake, and were necessary for setting up the TLS handshake to encrypt the connection between me (the client) and the server. Thus, data was securely transferred. 

I then filtered packets on Wireshark by using commands like:
    - ip.addr== to find traffic of particular ip addresses that were either the source or destination
    - ip.src== to find traffic of particular source ip addresses
    - ip.dst== to find traffic of particular destination ip addresses

I also learned to locate packets NOT containing certain addresses or ports. 
    - For example, using commands like !(ip.addr==...) to ignore certain packets from the capture.

Furthermore, I learned not get multiple packets from different sources like, for example, (tcp.port==80 or tcp.port==443) for HTTP and HTTPS traffic.

# Stateful-Inspection-Firewall-in-Linux

This firewall prototype was developed as my undergraduate project,in the domain of Cyber Security.

It is implemented using the Iptables framework of Linux. On this framework, system users can set commands to accept or reject incoming traffic. Further rules can be set, to classify packets from each other, based on port number, protocol followed, IP address etc. It is a method to enforce network security and can be implemented on any Linux kernel

## Resources Used
- CentOS Version 8 (It can be implemented on other flavours of Linux and is not restricted to CentOS alone)
- Iptables Framework
- https://www.netfilter.org/projects/iptables/index.html
- https://linux.die.net/man/8/iptables
## Firewall Chains 

There are few built-in chains that are included in tables. They are:

- INPUT :Traffic Incoming to the firewall-configured machine 

- FORWARD :The firewall-configyred machine acts as an intermedietary for network traffic between two devices

- OUTPUT :From the firewall-configured machine,to a specified device(identified by it's IP Address)

- PREROUTING :for modifying packets as they arrive.

- POSTROUTING :for modifying packets as they are leaving.

## Firewall Policies

- ACCEPT - Accept the packets
- DROP- Drop packets
- REJECT - Drop,but notify the sender that the packets have been dropped

## Rules Used

- Rule 1-iptables -A INPUT -s 8.8.8.8 -p tcp -j  ACCEPT

- Meaning-We wish to apply a rule on the INPUT to allow traffic from the IP Address 8.8.8.8 ,following TCP protocol
 
![4](https://user-images.githubusercontent.com/77625109/121905691-0dee6a00-cd48-11eb-9a56-19ca7f5b4493.png)

- Rule 2 -iptables -t filter -A OUTPUT -d 192.168.43.176 -j DROP

- Meaning-Apply a rule to the OUTPUT chain to drop all packets destined for 192.168.43.76

![5](https://user-images.githubusercontent.com/77625109/121907393-a46f5b00-cd49-11eb-948e-ed3adf5d3c32.png)

- Rule 3-iptables -A INPUT -s 192.168.43.176 -p tcp --dport 22 -j ACCEPT 

- Meaning-Accept all packets following tcp protocol,from the machine with IP=192.168.43.176, through the port 22(reserved for SSH) 

![Screenshot 2021-06-14 202726](https://user-images.githubusercontent.com/77625109/121913522-19915f00-cd4f-11eb-83bb-8ae904dbfaa6.png)

- Rule 4 -iptables --flush

- Meaning-Empty all rules from the firewall.It will now resemble a default unconfigured firewall 

![5](https://user-images.githubusercontent.com/77625109/121911306-48a6d100-cd4d-11eb-8f79-e62d460a4bc7.png)

## Testing Process


Using the built prototype,we tested both acceptance and denial of packets from certain ip’s,protocols and ports,on four different Linux systems.For uniformity,10 observational instances were recorded and it’s average is taken as the percentage.The results are given below:-

## Insights

These are the observations from our project:-

![One](https://user-images.githubusercontent.com/77625109/121900441-0bd5dc80-cd43-11eb-8fbe-7adc524505d8.png)


![Two](https://user-images.githubusercontent.com/77625109/121904699-0c707200-cd47-11eb-8d41-7580ba565666.png)


![Three](https://user-images.githubusercontent.com/77625109/121904752-18f4ca80-cd47-11eb-9065-44573e3a66da.png)

->To implement an iptables firewall :-

- Download the Linux distribution of your choice

- Have a virtualization software ready-prefereably VMWare or Oracle VirtualBox

- Set up your Linux machine on it and run upgrades

- Follow the commands as given above

## Conclusion

When developing a stateful inspection firewall,we have to keep in mind that it is ill-equipped to handle certain limitations,once configured and implemented. These limitations consist of:-
- Shadowed rules - (the rule that cannot match with any packet because a packet will be matched with other rules above) which can lead to security problems. 
- Limitations about swapping positions between rules can bring a change in firewall policy and cause security problem.Packet filters do not filter fragmented packets well and are stateless; they do not maintain any state information for added protection.

## What the future holds?

The biggest change over the last few years has been the rise and dominance of the “next gen” firewall.They are an advanced version of the traditional firewall that doesn’t merely block ports and IPs, NGFWs feature much smarter technology, combining IDS, anti-spam and more, offering a full spectrum of defense. They’re also “application aware” and much better suited to today’s app-centric world.



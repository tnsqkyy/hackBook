# Networking Overview

> This guide explains the basic idea of a computer network, why it's important, and how networks are all around us, in tech and in real life.

---

### 🌍 Part 1: What is a Network?

The main idea of a **network** is simple: it's all about **connection**. It's just a bunch of different things connected to each other. A good example is your group of friends—you're all connected by things you have in common.

This idea of connecting things isn't just for computers. You can see networks everywhere:

*   The bus or train routes in a city.
*   The power grid that brings electricity to our homes.
*   A neighborhood where people know each other.
*   The postal system that moves letters and packages.

When we talk about networking with computers, we're just doing the same thing, but with electronics. It's how your phone can grab information from the other side of the world. Networking is all about learning how these devices talk to each other and the rules (called **protocols**) they follow to make sure the conversation goes smoothly.

A computer network can be as small as two devices or as huge as the internet, which connects billions. The connected "things" on a network (**nodes**) can be regular computers and phones, or special tools like security cameras, smart traffic lights, and even smart farming equipment.

Because computer networks are a huge part of our daily lives—running everything from the weather forecast and power grids to traffic lights—**you can't be good at cybersecurity without understanding how networks work.**

---

### 🌐 Part 2: What is the Internet?

Now that we know a network is just a bunch of connected devices, what exactly *is* the Internet?

The **Internet** is one giant, worldwide network made up of many smaller networks all connected together. It's like a massive web linking millions of smaller networks.

<p align="center">
  <img src="./assets/images/internet_overview.png" alt="Internet Diagram" width="600"/>
  <br/>
  <em>Figure 1: How your laptop (Network B) connects to services like Github (Network A) and Google (Network C) via the Internet.</em>
</p>

To get a clearer picture, look at the diagram above. You can see how different private networks (like your home network) connect to the big "Internet cloud" to talk to services hosted in other networks.

The Internet started in the late 1960s as a U.S. military project called **ARPANET**. But the Internet we use today, with websites and links (the **World Wide Web** or **WWW**), was really born in 1989 when it was invented by Tim Berners-Lee. That's when it became a massive library for storing and sharing information.

So, how does this all fit together? Think of your home network (your laptop, phone, and smart TV) as a **private network**. It's your own little bubble. When you connect that bubble to the outside world (through your Internet Service Provider), you're joining a **public network**.

The Internet is just one giant public network made up of billions of smaller private networks all linked together. There are two main types of networks:

*   A **Private Network**: A network that is not connected to the internet (like a home or office network).
*   A **Public Network**: A network that is connected to the internet.

---

### 📍 Part 3: How Devices Talk (IP and MAC Addresses)

For devices to chat and keep things organized, they need a way to know who's who. Imagine trying to talk to someone if you don't even know their name!

Just like us, every device on a network has two main ways to be identified: a 'name' and a 'fingerprint'. You can change your name, but your fingerprints usually stay the same. Devices work similarly: one ID can change, but the other is pretty fixed.

#### **IP Addresses (Your Device's Changing 'Name')**

An **IP Address** is like a temporary home address for your device on the network. It's a set of numbers, usually four groups separated by dots (like `192.168.1.1`). How these numbers are chosen can get complicated (that's 'subnetting' for another day!).

The important thing is, while IP addresses can change (like moving to a new house), only one device can have that specific address on the same network at any given time.

Remember private and public networks? Your device will have a **private IP address** to talk to other devices on your home network, and a **public IP address** when it talks to the Internet. Your Internet provider (ISP) gives you your public IP address (and charges you for it!).

With so many devices online (Cisco once thought there'd be 50 billion by 2021!), finding unique public IP addresses is getting tough. That's because the original system, **IPv4**, only has about 4.29 billion addresses. Not enough for everyone!

**IPv6** is the newer system. It looks a bit scarier (it uses letters and numbers), but it has a mind-boggling number of addresses (340 *trillion* trillion trillion!), solving the IPv4 shortage. It's also more efficient.

#### **MAC Addresses (Your Device's Permanent 'Fingerprint')**

Every device that connects to a network (like your WiFi card) has a special, built-in "serial number" from the factory. This is called its **MAC (Media Access Control) address**.

It's a mix of numbers and letters, like `a4:c3:f0:85:ac:2d`. The first half tells you who made the device, and the second half is unique to that specific device.

But here's a trick: MAC addresses can be faked or 'spoofed'. This means one device can pretend to be another by using its MAC address.

This can fool poorly set-up security systems. Imagine a firewall set to trust only the admin's computer (by its MAC address). If a hacker 'spoofs' that MAC address, the firewall might think the hacker is the admin!

Some places like cafes use MAC addresses to control who gets on their WiFi (or charge more for faster speeds). There might even be a lab to try this out!

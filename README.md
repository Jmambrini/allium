# Allium

> _Allium_: a genus of monocotyledonous flowering plants to which onion species belongs.

Allium is a prototype implementation of the [Riffle](https://people.csail.mit.edu/devadas/pubs/riffle.pdf) anonymity network.
 
Currently, this project is being made **for study purposes only**, therefore, **it should not be used for any real anonymous communication.**

## How Allium works?

First, it is necessary to define the concepts of **Onion Routing** and **Mixnets**.

[Onion Routing](https://en.wikipedia.org/wiki/Onion_routing) is a technique that aims at the anonymity of communication between a computer network. For this, messages are encapsulated in encryption layers, hence the name onion routing, referring to the layers of an onion. The image below shows a message being sent with onion routing.

![Onion routing representation](https://upload.wikimedia.org/wikipedia/commons/e/e1/Onion_diagram.svg)

[MixNets](https://en.wikipedia.org/wiki/Mix_network) are routing protocols designed to make it difficult to track any message. They work as follows:

- The message, already encrypted in layers, is sent to the first MixNet server;
- Upon receiving this message, the server decrypts the first layer, and shuffles the order of the messages. After shuffling, send messages to the next server;
- The second server receives the messages, decrypts the second layer, shuffles the order of the messages, and sends them to the next server;
- Finally, the last server receives the messages, decrypts the last layer, and sends them to the receiver.

![MixNets representation](https://upload.wikimedia.org/wikipedia/commons/4/4f/Red_de_mezcla.png)

One of the problems found in MixNet is that the receiver is not anonymous, and if one of the servers is malicious, the anonymity of the sender is also compromised. To solve this, the Riffle protocol was developed.

Riffle consists of a small set of anonymous servers and a large number of users. It guarantees anonymity to all non-malicious users as long as there is at least one non-malicious server. The project uses a hybrid shuffling and a private receiving of information to achieve computational and bandwidth efficiency.
The **hybrid shuffling**  is used to prevent any alteration of messages by a malicious user or server. It works by having each server in the suite create mathematical proofs that the messages sent were handled in the expected way, not being altered according to a malicious agent. However, this process slows down the network due to heavy message traffic. For this, the authentication encryption technique is used.

An **encryption authentication** can verify the authenticity of an encrypted message, however, even being more efficient than the hybrid shuffle, it needs both the sender and the recipient to share a private encryption key.

![Anonymous File Sharing Protocol](https://uploads-ssl.webflow.com/61430f2787cc952cb53eec26/61430f2787cc95301a3eed75_Fig-2.-Anonymous-File-Sharing-Protocol.png)


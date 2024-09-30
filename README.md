# Secure Distributed Auction System

This project implements a distributed auction system using Java RMI (Remote Method Invocation). It allows users to create accounts, list items for sale, place bids, and manage auctions in a distributed environment. The system also employs asymmetric encryption (RSA) to ensure secure communication between users and the server.

## Features
- **Distributed System**: Built using Java RMI to allow multiple users to interact with the auction system remotely.
- **Auction Functionality**: Users can create items, place bids, and view active auctions.
- **Security**: Asymmetric encryption (RSA) is used to secure data transmissions between the server and clients.
- **Persistent User Data**: User data, including public/private keys, is stored for secure interactions.

## Technologies Used
- **Java RMI** for distributed architecture
- **RSA Encryption** for secure communication
- **Java Collections** for managing auctions and user data

## How to Run the Project Locally

### Prerequisites
- **Java 8+** installed
- **Maven** installed (if not already)
- Basic knowledge of Java RMI and encryption

### Step-by-Step Instructions

1. **Clone the Repository**:
```bash
git clone <repo-url>
cd Distributed-Auction-System
```
2. Generate RSA Key Pair: The system uses RSA public/private keys to secure communication. You need to generate these keys before running the server.

Generate a public/private key pair in Java:

```bash
KeyPairGenerator keyGen = KeyPairGenerator.getInstance("RSA");
keyGen.initialize(2048);
KeyPair pair = keyGen.generateKeyPair();
PrivateKey privateKey = pair.getPrivate();
PublicKey publicKey = pair.getPublic();
```

3. Compile and Run the Project:
First, compile the project using Maven or a Java IDE like IntelliJ IDEA:

```bash
nvm compile
```

4. Then start  RMI registry:
   
```bash
rmiregistry
```

5. After that, start the auction server:

```bash
java -cp target/classes/ com.example.auction.AuctionServer
```

6. To run the client, use the following command:

```bash
java -cp target/classes/ com.example.auction.AuctionClient
```

7. Configuring Public/Private Keys:

Ensure that the generated public and private key files (server_privateKey and server_publicKey) are present in the server's directory. The server will use these keys to decrypt data sent from clients and to sign outgoing messages.

8.Interacting with the Auction System:

Once the server is running, clients can register, create items for auction, bid on items, and view the list of available auctions.
The server handles secure communication using the RSA keys to ensure that all data sent between clients and the server is encrypted.

Troubleshooting

RMI Registry Issues: If you encounter issues with starting the rmiregistry, ensure that the port you're using is free and that your firewall allows Java RMI communication.
Key Generation Errors: If you encounter errors with key generation, make sure you have the correct Java security libraries and permissions to write to the file system.

Important Notes

Security: The project uses asymmetric encryption (RSA) for secure communication between the server and clients. Ensure you never expose your private key.
Keys: If you're deploying the system on multiple machines, distribute the public key to clients, but keep the private key secure on the server.

Future Enhancements

Improved Fault Tolerance: Implement passive replication or dynamic primary replica switching to handle server failures.
User Authentication: Add password-based authentication in addition to RSA encryption for user verification.
Persistent Storage: Integrate a database for storing auction items and user data instead of in-memory storage.

This project was created as part of a university module on distributed systems and demonstrates secure communication using Java RMI and encryption.

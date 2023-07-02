Hello, everyone, We will be discussing modern cryptography in general.

So Cryptography can be defined as the process of concealing the contents of a message from all except those who know the key during its transit or storage. Modern cryptosystems utilize computationally complex algorithms and long cryptographic keys to meet the Cryptographic Goals of confidentiality, integrity, authentication, and nonrepudiation.


Confidentiality

Confidentiality ensures that messages remain protected from disclosure to unauthorized individuals during transmission between two or more parties.

There are two main types of cryptosystems that enforce confidentiality:

1. Symmetric-key cryptosystems (make use of a shared secret key available to all users of the cryptosystem) and

2. Asymmetric-key cryptosystems or Public-key cryptosystems (utilize individual combinations of public and private keys for each user of the system).

Integrity

Integrity is a means to ensure that the message has remained unaltered (or not modified) from it was produced, while it was in transmission, and during storage. If integrity mechanisms are in place, the recipient of a message can be certain that the message received is identical to the message that was sent.

This protects against all forms of alteration: intentional alteration by a third party attempting to insert false information and unintentional alteration by faults in the transmission process. Message integrity is enforced through the use of digitally signed message digests created upon transmission of a message.

The recipient of the message simply verifies that the message’s digest and signature are valid, ensuring that the message was not altered in transit. Integrity can be enforced by both symmetric and asymmetric cryptosystems.

Authentication

Authentication provides assurances as to the identity of a user. One possible scheme that uses authentication is the challenge-response protocol, in which the remote user is asked to encrypt a message using a key known only to the communicating parties. Authentication is something you use to prove your identity such as something you have, know, or you are. Authentication can be achieved with both symmetric and asymmetric cryptosystems.

Nonrepudiation

Nonrepudiation provides assurance to the recipient that the message actually originated by the sender and not someone masquerading as the sender. It prevents the sender from subsequently denying that they never sent the message in the first place (also known as repudiating the message). Nonrepudiation is only possible with asymmetric cryptosystems.

Now let’s talk about symmetric-key cryptography …

Symmetric key cryptography

Symmetric key cryptography, also known as private key cryptography, utilizes a single key for both encryptions of the plaintext and decryption of the ciphertext. The key itself must be shared between the sender and the receiver. The same key on both ends of the communication is used to encrypt and decrypt messages. The symmetric in symmetric key cryptography is a reference to the use of a single key. The symmetric key encryption and decryption processes are illustrated in the Figure below.


Symmetric key cryptography has several weaknesses:

One of the chief weaknesses of symmetric key cryptography lies in the use of one key (or use of a single shared key. If the key is exposed beyond the sender and the receiver, it is possible for an attacker who has managed to intercept it to decrypt the message or, worse to decrypt the message, alter it, then encrypt it once more and pass it on to the receiver in place of the original message.

2. Key distribution is a major problem. Parties must have a secure method of exchanging the secret key before establishing communications with the symmetric key protocol. If a secure electronic channel is not available, an offline key distribution method must often be used (i.e., outof-band key exchange).

3. Symmetric key cryptography does not implement nonrepudiation. Symmetric key cryptography by itself provides only confidentiality, and not integrity, as we would not be aware that the message in our example had been altered. Because any communicating party can encrypt and decrypt messages with the shared secret key, there is no way to tell where a given message originated.

4. Keys must be regenerated often. Each time a participant leaves the group, all keys that involved that participant must be discarded.

5. The algorithm is not scalable. It is extremely difficult for large groups to communicate using symmetric key cryptography. Secure private communication between individuals in the group could be achieved only if each possible combination of users shared a private key.

Example of Key Requirements

The fact that symmetric cryptosystems require each pair of potential communicators to have a shared private key makes the algorithm nonscalable. The total number of keys required to completely connect n parties is given by the following formula:


Strength of symmetric key cryptography

The major strength of symmetric key cryptography is the great speed at which it can operate. Symmetric keying is very fast, often 1,000 to 10,000 times faster than asymmetric. By nature of the mathematics involved, symmetric-key cryptography also naturally lends itself to hardware implementations, creating the opportunity for even higher-speed operations.

Symmetric key algorithms

Some of the cryptographic algorithms that are more recognizable to the general public are symmetric key algorithms. Common symmetric cryptosystems:

1. Data Encryption Standard (DES),

2. Triple DES (3DES), and

3. Advanced Encryption Standard (AES).

Data Encryption Standard (DES)
Because DES is a block cipher, it segments the input data (or plaintext) into blocks.
DES processes 64-bits of plain text at a time to output 64-bit blocks of ciphertext.
DES uses a 56-bit key to drive the encryption and decryption process.
Because DES is based on symmetric-key cryptography, a block cipher uses the same key to encrypt and decrypt.
DES utilizes a long series of exclusive OR (XOR) operations to generate the ciphertext. This process is repeated 16 times for each encryption/decryption operation. Each repetition is commonly referred to as a “round” of encryption, explaining the statement that DES performs 16 rounds of encryption.
2. 3DES

The short key length which is a weakness of DES was compensated for a period of time through the use of 3DES (pronounced triple DES), which is simply DES used to encrypt each block three times, each time with a different key.

3. Advanced Encryption Standard (AES)

AES is a set of symmetric block ciphers endorsed by the US government (in Oct. 2000) through National Institute of Standards and Technology (NIST), and now used by a variety of other organizations, and is the replacement for DES as the standard encryption algorithm for the US federal government.

AES supports variable key-size : 128-bit key, one with a 192-bit key, and one with a 256-bit key.

The number of encryption rounds depends upon the key length chosen:

128-bit keys require 9 rounds of encryption.
192-bit keys require 11 rounds of encryption.
256-bit keys require 13 rounds of encryption.
Although symmetric key cryptography makes use of only one key, asymmetric key cryptography, is also known as public-key cryptography. In asymmetric key cryptography system, each user has two

keys:

1. a public key, which is shared with all users, and

2. a private key, which is kept secret and known only to the user.

AES Implementation in JavaScript

function encrypt(message = ‘’, key = ‘’){
var message = CryptoJS.AES.encrypt(message, key);
return message.toString();
}
function decrypt(message = ‘’, key = ‘’){
var code = CryptoJS.AES.decrypt(message, key);
var decryptedMessage = code.toString(CryptoJS.enc.Utf8);

return decryptedMessage;
}
console.log(encrypt(‘Hello World’));
console.log(decrypt(‘U2FsdGVkX1/0oPpnJ5S5XTELUonupdtYCdO91v+/SMs=’))

Asymmetric key algorithms

Several asymmetric algorithms exist, including:

RSA algorithm: is an asymmetric algorithm used all over the world, including in the Secure Sockets Layer (SSL) protocol, which is used to secure many common transactions such as Web and e-mail traffic. RSA was created in 1977 and is still one of the most widely used algorithms in the world to this day.
2. Elliptic curve cryptography (ECC): is a class of cryptographic algorithms, although it is sometimes referred to as though it were an algorithm in and of itself.

3. Diffie — Hellman: is a method for securely exchanging cryptographic keys over a public communications channel. Keys are not actually exchanged.

4. Digital Signature Standard (DSS): is a Federal Information Processing Standard specifying a suite of algorithms that can be used to generate digital signatures.

Stream Cipher encrypt data one byte (or bit) at a time using a key stream. A common simple example is using XOR with a pseudo-random key stream. 


1) DES (Data Encryption Standard)
•	Key and Encoding
•	Uses an 8-byte key, required by DES.
•	Encodes the Greek text with ISO 8859-7 to handle Greek characters.
•	Encryption (DES-ECB)
•	Pads the plaintext to match DES’s 8-byte block size.
•	Encrypts using DES in ECB mode.
•	Outputs the ciphertext in hexadecimal format.
•	Decryption
•	Decrypts the ciphertext.
•	Removes padding.
•	Decodes back to the original Greek text using ISO 8859-7.


2) AES (Advanced Encryption Standard)

•	Key Derivation
•	Derives a 32-byte AES key from a password using PBKDF2 with SHA-256 and a random 16-byte salt.
•	Encryption (AES-CBC)
•	Generates a random 16-byte IV.
•	Pads the plaintext using PKCS7 to match AES block size.
•	Encrypts the message with AES in CBC mode.
•	Concatenates salt, IV, and ciphertext, then encodes in Base64 for safe storage/transmission.
•	Decryption
•	Extracts the salt, IV, and ciphertext from the Base64-encoded input.
•	Re-derives the AES key from the password and salt.
•	Decrypts and unpads the message to recover the original plaintext.
•	Example
•	Input: "Γειά σου Κόσμε" (“Hello World” in Greek).
•	Output: Encrypted Base64 string and successfully decrypted original text.

3) RC4 (Rivest Cipher)
This script implements a stream cipher encryption and decryption, very similar to RC4, using Python:
•	Input and Parameters
•	plain_text and key are given as binary strings.
•	n defines how many bits are processed at a time.
•	State Vector Initialization (S)
•	An array S is initialized from 0 to 2^n - 1.
•	Key Scheduling Algorithm (KSA)
•	The state vector S is permuted using the key to produce an initial permutation.
•	Pseudo-Random Generation Algorithm (PRGA)
•	Generates a key stream from the permuted state vector.
•	Encryption
•	Each plaintext block is XORed with the key stream to produce the ciphertext.
•	Outputs the ciphertext as a binary string.
•	Decryption
•	Uses the same KSA and PRGA algorithms.
•	XORs the ciphertext with the key stream to recover the original plaintext.

4) RSA (Rivest–Shamir–Adleman)
   •	Key Generation
•	Selects two prime numbers p and q.
•	Computes n = p * q and Euler’s totient phi = (p-1)*(q-1).
•	Chooses e such that gcd(e, phi) = 1.
•	Computes d as the modular inverse of e modulo phi.
•	Outputs the public key (e, n) and private key (d, n).
•	Encryption
•	Converts each character of the plaintext to its ASCII value.
•	Computes ciphertext = (char^e) mod n for each character.
•	Decryption
•	Computes plaintext = (cipher_char^d) mod n for each number in the ciphertext.
•	Converts the numbers back to characters to recover the original message.
•	Example
•	Message "HELLO" is encrypted using the public key and successfully decrypted using the private key.


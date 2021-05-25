# Cryptography, authentication, identity 

- Encryption vs Encoding vs Hashing vs Obfuscation vs Signing
	- Be able to explain the differences between these things. 
	- [Various attack models (e.g. chosen-plaintext attack)](https://en.wikipedia.org/wiki/Attack_model).
	- Encryption can involve hashing, signing etc. Process of altering information for sending
	- Encoding, converting symbols to a different value (e.g. " %22 in URL-encoding)
	- Hashing, for passwords. Irreversable. Hash the same value to determine if the same.
	- Obfuscation, making things more difficult to read. The values are still the same, just represented in a more complex way that is not readable to the human eye/takes some time to process.
	- Signing, using an individuals private key to sign a message for non-repudation and integrity of messages.

- Encryption standards + implementations
	- [RSA (asymmetrical)](https://en.wikipedia.org/wiki/RSA_(cryptosystem)).
	- [AES (symmetrical)](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard).
	- [ECC (namely ed25519) (asymmetric)](https://en.wikipedia.org/wiki/EdDSA).
	- [Chacha/Salsa (symmetric)](https://en.wikipedia.org/wiki/Salsa20#ChaCha_variant).

- Asymmetric vs symmetric
	- Asymmetric is slow, but good for establishing a trusted connection. Private and Public Key
	- Symmetric has a shared key and is faster. Protocols often use asymmetric to transfer symmetric key. (one key)
	- Perfect forward secrecy - eg Signal uses this.

- Cyphers
	- [Block vs stream ciphers](https://en.wikipedia.org/wiki/Cipher).
	- [Block cipher modes of operation](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation).
	- [AES-GCM](https://en.wikipedia.org/wiki/Galois/Counter_Mode).

- Trusted Platform Module 
	- (TPM)
	- Trusted storage for certs and auth data locally on device/host.

- Integrity and authenticity primitives
	- [Hashing functions, e.g. MD5, Sha-1, BLAKE](https://en.wikipedia.org/wiki/Cryptographic_hash_function). Used for identifiers, very useful for fingerprinting malware samples.
	- [Message Authentication Codes (MACs)](https://en.wikipedia.org/wiki/Message_authentication_code).
	- [Keyed-hash MAC (HMAC)](https://en.wikipedia.org/wiki/HMAC).

- Entropy
	- PRNG (pseudo random number generators).
	- Entropy buffer draining.
	- Methods of filling entropy buffer.

- Certificates 
	- What info do certs contain, how are they signed? 
	- Look at DigiNotar.

- O-auth
	- Bearer tokens, this can be stolen and used, just like cookies.

- Auth Cookies
	- Client side.

- Sessions 
	- Server side.

- Auth systems 
	- SAMLv2o.
	- OpenID.

- Biometrics
	- Can't rotate unlike passwords.

- Password management
	- Rotating passwords (and why this is bad). 
	- Different password lockers. 

- U2F / FIDO
	- Eg. Yubikeys.
	- Helps prevent successful phishing of credentials.

- Compare and contrast multi-factor auth methods

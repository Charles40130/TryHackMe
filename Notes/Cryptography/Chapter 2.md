
Symetric Ciphers :
- Block Ciphers
- Stream Ciphers


Stream Ciphers :
- Encrypt bits individually
- Usually small and fast -> common in embedded device ( A5/1 for GSM phones)

Block Ciphers
- Always encrypt a full block (several bits)
- Are common for Internet applications

---
#### Focus on Stream Cipher
- Encryption yi = esi(xi ) = xi + si mod 2                      xi , yi , si
∈ {0,1}
- Decryption : xi = esi(yi ) = yi + si mod 2

Synchronous vs Asynchronous Stream Cipher
- security of stream cipher depends entirelity on the key stream

###### Synchronous Stream Cipher
- Key stream depend only on the key ( and possibly an initialization vector IV)
###### Asynchronous Stream Cipher
- Key stream depends also on the ciphertext ( dotted feedback enabled)

##### Stream Cipher : Throughput

----
### Random Number Generators ( RNGs )
- True RNG
- Pseudorandom RG
- Cryptographically Secure RNG

##### True RNG
- Based on physical random processes: coin flipping, dice rolling, semiconductor noise, radioactive decay, mouse movement, clock jitter of digital circuits
- Output stream si should have good statistical properties: Pr(si = 0) = Pr(si = 1) = 50% (often achieved by post-processing)
- Output can neither be predicted nor be reproduced

##### Pseudorandom Number Generator (PNRG)
- Generate sequences from initial seed value
- Typically, output stream has good statistical properties
- Output can be reproduced and can be predicted
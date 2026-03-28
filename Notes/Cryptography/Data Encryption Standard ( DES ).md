
2 primitive operations :
1. Confusion : an encryption operation where the **relationship between key and ciphertext is obscured**
2. Diffusion : an encryption operation where the **influence of one plaintext symbol is spread over many ciphertext symbols** with the goal of hiding statistical properties of the plaintext

* encrypts block of size 64 bits
* use key of size 56 bits
* symmetric cipher : same key for encryption and decryption
* ''

---
###### THE DES Feistel Network (1)

$L_{i} = R_{i-1}$
$R_{i} = L_{i-1} \oplus f(R_{i-1}, k_i)$

---
###### Internal Structure of DES
4 Steps :
1. Expansion E
2. XOR with round key
3. S-box substitution
4. Permuteation

---
64 Bits : 56 bits key and 8 bit parity

Security of DES
1. Key space is too small (2⁵⁶ keys)
2. S-box design criteria have been kept secret :
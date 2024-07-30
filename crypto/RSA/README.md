# Challenge Name: RSA Decryption Challenge
## Description:
We intercepted some encrypted messages but lost the private key. We do have the public key and the encrypted messages. Can you help us decrypt the messages and find the hidden flag?
## Public Key:
e=207 <br>
n=1921
## Ciphertext:
c=[1223, 1733, 927, 1900, 1223, 1643, 132, 571, 1733, 1765, 182, 500, 1453, 182, 266, 298, 1225, 1453, 1765, 1192, 1225, 717]
## Solution:
1. Factorize n to find p and q
2. Compute z using z = (p-1)(q-1)
3. Compute private key (d)=e^-1 mod z
4. Decrypt each number in c using m=c^d mod n<br>
```
e=207
n=1921
c=[1223, 1733, 927, 1900, 1223, 1643, 132, 571, 1733, 1765, 182, 500, 1453, 182, 266, 298, 1225, 1453, 1765, 1192, 1225, 717]
l=[]
for i in range(2,n):
  if(n%i==0):
    l.append(i)

z=(l[0]-1)*(l[1]-1)
d=pow(e,-1,z)
decrypt=''.join(chr(pow((char),d,n)) for char in c)
print(f"plain text: {decrypt}")
```
``` plain text: CTF{CRYPTO_IS_AWESOME} ```

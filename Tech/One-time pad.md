# Definition

One-time pad uses a randomly generated sequence of bits to use as keys for both encryption and decryption of a message. The encryption and decryption process are [XOR](XOR.md) operators.

# Pros and cons

## Pros

- Can achieve *perfect security* if implemented
- If successfully implemented, basically the whole crypto problem is solved

## Cons

- Extremely computationally expensive
- Workarounds for the above problem introduce security flaws
>- Using deterministic models for key generation instead of true randomness
>- Reusing keys -> Multi-time pad
>-> If a cipher text $C$ and corresponding plain text $P$ is known, the key $K$ can be retrieved by $C \oplus P = K$.
>-> ***Crib dragging***: If a cipher text $C$ is known and part of the corresponding plain text $p_i$ is known, part of the key $k_i$ can be retrieved by $c_i \oplus p_i = k_i$. An attacker can use common known plain text phrases to guess a plain text message.
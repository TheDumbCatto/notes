[Key stretching](https://en.wikipedia.org/wiki/Key_stretching)is a method of strengthening a potentially weak key/password. The basic steps might include:
- salting ($S$) the plaintext secret ($P$): $P||S$
- then hashing that salted plaintext in multiple iterations, usually tens of thousands iterations: $H(1) = hash(P||S);\ H(2) = hash(H1);\ ...\ ;\ H(10000) = hash(H9999)$
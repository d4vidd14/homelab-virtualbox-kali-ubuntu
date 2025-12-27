## Lab 02 — DNS basics (dig)

### Goal
Practice DNS queries commonly used during reconnaissance: A/AAAA, MX, TXT and reverse DNS (PTR).

### Commands used
```bash
dig example.com A +noall +answer
dig example.com AAAA +noall +answer
dig google.com MX +noall +answer
dig google.com TXT +noall +answer
dig -x 1.1.1.1 +noall +answer

# Computational Theory: SHA-256

This repository holds my work for the Computational Theory module. The notebook `problems.ipynb` builds the SHA-256 hash function from FIPS 180-4 step by step in Python and NumPy, and checks each step against the standard.

## Contents

- `problems.ipynb`: the notebook, with six problems.
  1. Representing SHA-256 Data: 32-bit words, word arrays, messages, blocks and byte order
  2. SHA-256 Bitwise Operations: the six functions of Section 4.1.2
  3. Generating the SHA-256 Constants: the 64 constants K, computed from the cube roots of primes and checked against the standard
  4. Padding and Parsing Messages: `pad(msg)` and the `block_parse(msg)` generator, tested at the padding boundaries and on the files in `data/`
  5. The SHA-256 Compression Function: H⁽⁰⁾, the message schedule, the 64 rounds and the hash update, checked against NIST's worked examples
  6. Complete SHA-256: `sha256(msg)`, tested against Python's `hashlib`
- `data/`: test files from the module notes (empty, `abc` and 128 bytes)
- `.gitattributes`: keeps the test files byte-for-byte, so Windows line endings don't change their hashes
- `requirements.txt`: the Python packages needed (NumPy and Jupyter Notebook)

## Getting started

Requires Python 3.11 or later.

### Clone

```bash
git clone https://github.com/MartyHughes1/computationaltheory
cd computationaltheory
```

### Set up and run

With [uv](https://docs.astral.sh/uv/):

```bash
uv venv
source .venv/bin/activate # Windows: .venv\Scripts\activate
uv pip install -r requirements.txt
jupyter notebook problems.ipynb
```

Without uv, plain `pip` works the same way:

```bash
python -m venv .venv
source .venv/bin/activate # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook problems.ipynb
```

When the notebook opens, choose **Kernel → Restart Kernel and Run All Cells**. Each section ends with tests against FIPS 180-4, NIST's worked examples or `hashlib`, so if every cell runs without an `AssertionError`, the implementation is correct. The full run takes about 15 seconds, most of it the one-million-byte test in Problem 6.

## References

- NIST, [*FIPS 180-4: Secure Hash Standard*](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)
- NIST, [*Examples with Intermediate Values: SHA-256*](https://csrc.nist.gov/CSRC/media/Projects/Cryptographic-Standards-and-Guidelines/documents/examples/SHA256.pdf)
- McLoughlin, Computational Theory module repository: <https://github.com/ianmcloughlin/computational-theory>
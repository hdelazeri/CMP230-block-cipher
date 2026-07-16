# CMP230 Block Cipher

[Português](README.pt.md)

Academic activity for **CMP230** (Cryptography) at [INF/UFRGS](https://www.inf.ufrgs.br/).

This project implements a block cipher by chaining three classical ciphers in sequence. Encryption applies the chain forward; decryption applies it in reverse. The full pipeline runs five rounds.

## Ciphers

| Order (encrypt) | Cipher | Role |
|-----------------|--------|------|
| 1 | [Rail Fence](rail_fence.py) | Transposition (zigzag rails) |
| 2 | [ADFGVX](adfgvx.py) | Substitution + columnar transposition |
| 3 | [Alberti](alberti.py) | Polyalphabetic substitution |

Decrypt order: Alberti → ADFGVX → Rail Fence.

## Requirements

- Python 3 (no third-party packages)

A [Dev Container](.devcontainer/devcontainer.json) with Python 3.12 is included if you prefer that setup.

## Usage

```bash
python main.py cipher -k KEY -i plaintext.txt -o ciphertext.txt
python main.py decipher -k KEY -i ciphertext.txt -o plaintext.txt
```

| Argument | Description |
|----------|-------------|
| `cipher` / `decipher` | Encrypt or decrypt |
| `-k`, `--key` | Shared secret key (required) |
| `-i`, `--input` | Input file (default: stdin) |
| `-o`, `--output` | Output file (default: stdout) |

Input is normalized to uppercase. Examples with pipes:

```bash
echo "HELLO WORLD" | python main.py cipher -k SECRET
echo "HELLO WORLD" | python main.py cipher -k SECRET | python main.py decipher -k SECRET
```

## Project layout

```
├── main.py           # CLI and round orchestration
├── rail_fence.py     # Rail Fence cipher
├── adfgvx.py         # ADFGVX cipher
├── alberti.py        # Alberti cipher
└── .devcontainer/    # Optional VS Code / Codespaces environment
```

## License

Academic coursework for CMP230 at INF/UFRGS.

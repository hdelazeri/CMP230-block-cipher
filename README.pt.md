# Cifra de Bloco — CMP230

[English](README.md)

Atividade acadêmica da disciplina **CMP230** (Criptografia) no [INF/UFRGS](https://www.inf.ufrgs.br/).

Este projeto implementa uma cifra de bloco combinando três cifras clássicas em sequência. A cifragem aplica a cadeia na ordem direta; a decifragem, na ordem inversa. O pipeline completo é executado em cinco rodadas.

## Cifras

| Ordem (cifrar) | Cifra | Papel |
|----------------|-------|-------|
| 1 | [Rail Fence](rail_fence.py) | Transposição (trilhos em zigue-zague) |
| 2 | [ADFGVX](adfgvx.py) | Substituição + transposição colunar |
| 3 | [Alberti](alberti.py) | Substituição polialfabética |

Ordem na decifragem: Alberti → ADFGVX → Rail Fence.

## Requisitos

- Python 3 (sem pacotes de terceiros)

Há um [Dev Container](.devcontainer/devcontainer.json) com Python 3.12 caso prefira esse ambiente.

## Uso

```bash
python main.py cipher -k CHAVE -i texto.txt -o cifrado.txt
python main.py decipher -k CHAVE -i cifrado.txt -o texto.txt
```

| Argumento | Descrição |
|-----------|-----------|
| `cipher` / `decipher` | Cifrar ou decifrar |
| `-k`, `--key` | Chave secreta compartilhada (obrigatória) |
| `-i`, `--input` | Arquivo de entrada (padrão: stdin) |
| `-o`, `--output` | Arquivo de saída (padrão: stdout) |

A entrada é normalizada para maiúsculas. Exemplos com pipes:

```bash
echo "HELLO WORLD" | python main.py cipher -k SECRET
echo "HELLO WORLD" | python main.py cipher -k SECRET | python main.py decipher -k SECRET
```

## Estrutura do projeto

```
├── main.py           # CLI e orquestração das rodadas
├── rail_fence.py     # Cifra Rail Fence
├── adfgvx.py         # Cifra ADFGVX
├── alberti.py        # Cifra de Alberti
└── .devcontainer/    # Ambiente opcional VS Code / Codespaces
```

## Licença

Trabalho acadêmico da disciplina CMP230 no INF/UFRGS.

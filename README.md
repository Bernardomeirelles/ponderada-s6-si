# Pesquisa e Implementação de SHA-256 e AES-256 em Python

## 1. Pesquisa e Seleção de Bibliotecas

### Descrição

Para implementar os algoritmos de hash SHA-256 e de criptografia AES-256 em Python, foram identificadas as seguintes bibliotecas:

- **`hashlib`**: Biblioteca padrão do Python que fornece interfaces para algoritmos de hash seguros, incluindo SHA-256.
- **`PyCryptodome`**: Biblioteca externa que oferece primitivas criptográficas de baixo nível, incluindo implementações do AES-256.

### Bibliotecas Selecionadas

1. **`hashlib`** (para SHA-256)
   - **Descrição**: O módulo `hashlib` implementa uma interface comum para muitos algoritmos de hash seguros e funções de resumo de mensagens. Inclui os algoritmos de hash seguros FIPS, como SHA1, SHA224, SHA256, SHA384, SHA512 (definidos no padrão FIPS 180-4), a série SHA-3 (definida no padrão FIPS 202), bem como o algoritmo MD5 da RSA (definido no RFC 1321 da internet). Os termos "hash seguro" e "resumo de mensagem" são intercambiáveis. Algoritmos mais antigos eram chamados de resumos de mensagem; o termo moderno é hash seguro.
   - **Documentação Oficial**: [hashlib — Secure hashes and message digests — Python 3.13.2 documentation](https://docs.python.org/3/library/hashlib.html)

2. **`PyCryptodome`** (para AES-256)
   - **Descrição**: O PyCryptodome é um pacote Python autossuficiente de primitivas criptográficas de baixo nível. Ele suporta Python 2.7, Python 3.6 e versões mais recentes, além de PyPy. O PyCryptodome é um fork do PyCrypto e traz várias melhorias em relação à última versão oficial do PyCrypto (2.6.1), como modos de criptografia autenticada (GCM, CCM, EAX, SIV, OCB), AES acelerado em plataformas Intel via AES-NI, suporte de primeira classe para PyPy e criptografia de curvas elípticas (curvas NIST P; Ed25519, Ed448, Curve25519).
   - **Documentação Oficial**: [PyCryptodome's documentation](https://pycryptodome.readthedocs.io/)


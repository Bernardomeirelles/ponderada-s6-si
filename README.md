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

   # ponderada-s6-si

## 2. Definição e Desenvolvimento dos Testes

### Cenários de Teste para SHA-256 e AES-256

#### Cenários para SHA-256 (Utilizando a biblioteca `hashlib`)

##### [Link do notebook para SHA-256 ](https://colab.research.google.com/drive/1_BH0Wah_RtehOqif_4v6dGgV-aRJuVMW?usp=sharing)

#### Teste 1 – Hash de String Simples
- **Objetivo:**  
  Verificar o hash de uma string curta.
- **Entrada:**  
  `"teste"`
- **Saída Esperada:**  
  Hash hexadecimal consistente .

#### Teste 2 – Hash de Texto Longo
- **Objetivo:**  
  Avaliar a performance e consistência com textos maiores.
- **Entrada:**  
  Um trecho de texto longo (por exemplo, "O professor Hayashi passou uma atividade.").
- **Saída Esperada:**  
  Um hash hexadecimal único correspondente ao conteúdo.

#### Teste 3 – Hash de Dados Binários
- **Objetivo:**  
  Testar a função com dados binários (ex.: bytes aleatórios).
- **Entrada:**  
  1KB de bytes aleatórios.
- **Saída Esperada:**  
  Hash hexadecimal, garantindo que dados binários sejam tratados corretamente.

#### Teste 4 – Idempotência do Hash
- **Objetivo:**  
  Confirmar que a mesma entrada gera sempre o mesmo hash.
- **Entrada:**  
  A string `"senha123"`, repetida 5 vezes.
- **Saída Esperada:**  
  O mesmo hash para cada execução.

#### Teste 5 – Hash de Conteúdo de Arquivo Simulado
- **Objetivo:**  
  Simular a leitura de um arquivo e calcular seu hash.
- **Entrada:**  
  100KB de dados (pode ser gerado aleatoriamente ou um arquivo de teste).
- **Saída Esperada:**  
  Hash hexadecimal único para os dados do “arquivo”.

---

#### Cenários para AES-256 (Utilizando a biblioteca `pycryptodome`)

##### [Link do notebook para AES-256 ](https://colab.research.google.com/drive/1jpS7r8NvpBnSjkD56Yx55QvcOTWbBt8k?usp=sharing)

#### Teste 6 – Encriptação em Modo ECB com String Simples
- **Objetivo:**  
  Testar a encriptação de uma string simples em modo ECB.
- **Entrada:**  
  A string `"teste"` e uma chave de 32 bytes.
- **Saída Esperada:**  
  Texto encriptado em formato hexadecimal (observando que o modo ECB não utiliza vetor de inicialização).

#### Teste 7 – Encriptação em Modo CBC com String Simples
- **Objetivo:**  
  Encriptar uma string simples utilizando o modo CBC, que requer um IV.
- **Entrada:**  
  A string `"teste"`, chave de 32 bytes e um IV aleatório.
- **Saída Esperada:**  
  Texto encriptado com IV embutido ou disponibilizado separadamente.

#### Teste 8 – Ciclo de Encriptação e Decriptação
- **Objetivo:**  
  Garantir que o texto encriptado pode ser decriptado corretamente.
- **Entrada:**  
  A string `"professor"`, utilizando AES-256 (modo CBC, por exemplo) com chave e IV.
- **Saída Esperada:**  
  Texto original `"professor"` recuperado após decriptação.

#### Teste 9 – Encriptação de Dados Binários com Medição de Tempo
- **Objetivo:**  
  Avaliar a performance da encriptação de 1KB de dados binários.
- **Entrada:**  
  1KB de bytes aleatórios, chave e IV para modo CBC.
- **Saída Esperada:**  
  Texto encriptado e tempo de execução registrado (em milissegundos).

#### Teste 10 – Iterações de Encriptação/Decriptação para Avaliação de Performance
- **Objetivo:**  
  Verificar o desempenho ao executar 100 ciclos de encriptação e decriptação.
- **Entrada:**  
  Uma string (por exemplo, `"teste performance"`), chave e IV, repetindo 100 vezes o ciclo de encriptação/decriptação.
- **Saída Esperada:**  
  Média do tempo de execução por iteração e confirmação de que o texto original é recuperado.
 
## Conclusão Comparativa entre SHA-256 e AES-256

O SHA-256 é um algoritmo de hash criptográfico unidirecional, utilizado principalmente para garantir a integridade e autenticidade de dados. Já o AES-256 é um algoritmo de criptografia simétrica, projetado para proteger informações confidenciais, permitindo tanto a encriptação quanto a recuperação dos dados originais mediante uma chave secreta.

Nos testes realizados, o SHA-256 demonstrou ser altamente eficaz na verificação de integridade. No teste 4 (idempotência do hash), verificamos que a mesma entrada sempre gerou o mesmo hash, confirmando sua deterministicidade. Além disso, no teste 2 (hash de texto longo), pequenas mudanças na entrada resultaram em hashes completamente distintos, validando o efeito avalanche, um princípio para garantir que nenhuma informação da entrada possa ser inferida a partir do hash gerado.

Outro aspecto importante do SHA-256, observado no teste 5 (hash de conteúdo de arquivo simulado), é sua capacidade de gerar resumos criptográficos únicos para qualquer tipo de dado, incluindo arquivos inteiros. Isso o torna uma escolha ideal para aplicações que exigem verificação de integridade, como autenticação de documentos e armazenamento seguro de senhas. Entretanto, por ser um algoritmo unidirecional, os dados originais nunca podem ser recuperados a partir do hash, limitando seu uso a situações em que a reversibilidade não é necessária.

O AES-256, por sua vez, mostrou-se eficiente para a proteção de informações sensíveis, garantindo que apenas usuários autorizados, com a chave correta, possam acessar os dados criptografados. Durante os testes, foi possível observar que diferentes modos de operação afetam a segurança do processo. No teste 6 (encriptação em modo ECB), identificamos que esse modo não introduz variação entre blocos idênticos, o que pode comprometer a segurança em certos cenários. Já no teste 7 (encriptação em modo CBC), o uso de um vetor de inicialização adicionou aleatoriedade à saída, tornando os dados cifrados mais seguros contra padrões previsíveis.

Além disso, o teste 8 (ciclo de encriptação e decriptação) confirmou que o AES-256 permite recuperar integralmente as informações criptografadas, algo impossível no SHA-256. Isso torna o AES-256 uma solução ideal para o armazenamento seguro de dados sigilosos e para a comunicação protegida entre sistemas. No entanto, sua segurança depende diretamente da proteção da chave de criptografia. Se a chave for comprometida, qualquer pessoa poderá descriptografar as informações.

### Diferenças Principais e Aplicações

SHA-256 é um algoritmo eficiente para garantir que um dado permaneça autêntico e inalterado. Seu uso é recomendado para assinaturas digitais, autenticação e verificação de arquivos. Por outro lado, AES-256 é eficiente para a proteção de informações contra acessos não autorizados, garantindo que apenas quem possui a chave correta possa acessar o conteúdo.

A escolha entre SHA-256 e AES-256 depende do objetivo final. Se a necessidade for garantir que um dado não foi modificado, o SHA-256 é a melhor opção. Se o foco for proteger informações sigilosas e garantir que possam ser recuperadas posteriormente, o AES-256 é a alternativa mais adequada.

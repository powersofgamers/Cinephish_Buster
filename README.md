# Cinephish_Buster
🎬 CinePhish Buster — Caça-Fantasmas dos Codecs &amp; Inspetor de Mídia

O **CinePhish Buster** é um utilitário em Python projetado para escanear diretórios em busca de arquivos de vídeo de todas as extensões conhecidas, mitigando riscos de segurança associados a arquivos mascarados, injeções binárias ou overlays maliciosos. 

O foco da ferramenta é o **Isolamento e Análise Segura (Content Disarm and Reconstruction - CDR)**, garantindo que arquivos suspeitos sejam neutralizados antes de qualquer tentativa de reprodução.

---

## 🚀 Como Instalar

Este script utiliza predominantemente bibliotecas nativas do Python (`os`, `shutil`, `hashlib`, `pathlib`), o que o torna altamente portátil para **Linux, Windows e macOS/iOS**.

### Pré-requisitos
Certifique-se de ter o Python 3.10 ou superior instalado em sua máquina.

1. **Clone ou baixe o script** para o seu ambiente local:
   git clone https://github.com/powersofgamers/Cinephish_Buster
   cd cinephish-buster


 2. *(Opcional)* Se você planeja compilar o script em um executável binário independente (como mostrado nos logs do PyInstaller), instale a dependência necessária:

   pip install pyinstaller
   
   
## 📂 Estrutura de Pastas e Funcionamento
Ao ser executado pela primeira vez, o programa gerencia e cria automaticamente uma árvore de diretórios dedicada à segurança. Entenda para que serve cada uma:
text
📂 cinephish-buster/
├── 📄 CinePhish_Buster.py     # Script principal do programa
├── 📂 meus_videos_teste/      # 📥 PASTA DE ENTRADA: Coloque seus vídeos aqui
├── 📂 quarentena_cinephish/   # 🔒 QUARENTENA: Vídeos suspeitos isolados
└── 📂 analise_texto/          # 🔬 ANÁLISE: Dumps textuais seguros (.txt)


### 📥 meus_videos_teste/
Esta é a **pasta de entrada** do programa. Todos os vídeos que você deseja analisar devem ser colocados aqui dentro antes de iniciar a varredura. O script faz uma busca recursiva, o que significa que ele também lerá vídeos que estiverem organizados dentro de subpastas nesta árvore.
### 🔒 quarentena_cinephish/ (Quarentena)
Se o programa detectar qualquer anomalia estrutural no arquivo de mídia (como uma extensão falsa, tamanho incompatível com arquivos de vídeo reais ou payloads embutidos), o arquivo é **removido imediatamente** da pasta original e movido para cá.
> **Nota de Segurança:** Isolar o arquivo impede que ele seja aberto acidentalmente por players de mídia vulneráveis do sistema operacional.
> 
### 🔬 analise_texto/ (Análise de Texto)
Após isolar o arquivo na Quarentena, o CinePhish Buster realiza uma extração de strings legíveis baseada em caracteres ASCII (comportando-se de forma semelhante ao comando strings de sistemas Unix). Ele gera um arquivo .txt contendo a assinatura SHA-256 e os dados decodificados da mídia.
 * **Para que serve:** Você pode abrir esse arquivo .txt com qualquer editor de texto comum para inspecionar metadados, procurar por URLs maliciosas externas ou comandos injetados (como powershell, cmd.exe, scripts bash), com a total segurança de que o código binário não será executado.
 * 
## 💻 Como Executar
### 1. Preparação
Cole os arquivos de vídeo (como .mp4, .mkv, .avi, etc.) dentro do diretório ./meus_videos_teste.
### 2. Execução Direta (Python)
No terminal, execute o seguinte comando:

python CinePhish_Buster.py

## 🛠️ Tecnologias Utilizadas
 * **Python 3** (Multiplataforma)
 * **Pathlib** (Garantiu compatibilidade nativa de caminhos no Windows e sistemas POSIX)
 * **Hashlib** (Cálculo de hashes criptográficos SHA-256 para checagem de integridade)
*Aviso: Este utilitário foi desenhado para fins de pesquisa, automação de segurança e gerenciamento defensivo de laboratórios de TI.*

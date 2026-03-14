# Como configurar/instalar/usar o `tesseract OCR` no `Linux Ubuntu`

## Resumo

Neste documento estão contidos os principais comandos e configurações para configurar/instalar/usar o `tesseract OCR` no `Linux Ubuntu`.

## _Abstract_

_In this document are contained the main commands and settings to set up/install/use the `tesseract OCR` on `Linux Ubuntu`._

## Descrição [2]

### `tesseract OCR`

O `tesseract OCR` é um reconhecedor óptico de caracteres (OCR) de código aberto desenvolvido originalmente pelo Google e posteriormente mantido como um projeto de código aberto. Sua principal finalidade é converter texto contido em imagens ou documentos digitalizados em texto legível por máquina. O `tesseract OCR` é amplamente utilizado para tarefas de extração de texto, como digitalização de documentos, conversão de imagens em texto pesquisável, automação de processos de entrada de dados e muito mais. Ele suporta uma variedade de idiomas e pode ser estendido com modelos de treinamento personalizados para melhorar o reconhecimento de caracteres em línguas específicas. Sua versatilidade e código aberto tornam-no uma escolha popular para empresas e desenvolvedores que precisam de recursos de OCR confiáveis em seus aplicativos e sistemas.

### `gImageReader`

O `gImageReader` é uma aplicação de código aberto que oferece uma _interface_ amigável para a extração de texto de imagens ou arquivos `.pdf`. Ele utiliza tecnologias de reconhecimento óptico de caracteres (OCR) para digitalizar documentos e converter o texto contido neles em formato editável. Com recursos como suporte a vários idiomas e opções de formatação, o gImageReader é uma ferramenta útil para transformar documentos digitalizados em texto pesquisável e editável.

### `translate-shell`

O `translate-shell` é uma ferramenta de linha de comando de código aberto que oferece a capacidade de traduzir texto e palavras entre vários idiomas diretamente do `Terminal Emulator`. Ele utiliza serviços de tradução _online_, como o `Google Translate`, para fornecer traduções rápidas e precisas. O `translate-shell` suporta uma ampla variedade de idiomas e pode ser usado tanto para traduções simples de palavras e frases quanto para traduções mais complexas de texto completo. Além disso, ele oferece opções avançadas, como tradução de áudio, detecção automática de idioma e pronúncia de palavras, tornando-se uma ferramenta útil para estudantes, viajantes e qualquer pessoa que precise de traduções instantâneas e convenientes diretamente do `Terminal Emulator`.

### `pdftotext`

O `pdftotext` é uma ferramenta de linha de comando, geralmente parte do pacote `Poppler` ou `Xpdf`, que converte o conteúdo de arquivos PDF em texto simples. Ele extrai o texto mantendo a ordem de leitura e pode preservar ou não a formatação de colunas e quebras de linha, conforme opções configuráveis. É muito útil para automatizar a extração de texto de documentos PDF em _scripts_ e fluxos de trabalho de análise de dados ou indexação.

### `pdfimages`

O `pdfimages` é uma ferramenta para extrair imagens de arquivos PDF. Caso seu PDF contenha imagens e você queira extraí-las, pode ser útil antes de uma conversão com `OCR`, como no caso de um PDF digitalizado.

### `qpdf`

O `qpdf` é uma ferramenta para manipular arquivos PDF de maneira avançada. Você pode usá-lo para fazer operações como quebra de PDFs, mesclagem, e até mesmo para manipular metadados.

### `pdfunite`

O `pdfunite` é uma ferramenta de linha de comando, integrante do pacote `poppler`, que permite mesclar vários arquivos PDF em um único documento. Basta informar na chamada os arquivos de entrada e o nome do PDF de saída. É ideal para scripts e fluxos de trabalho automatizados de organização e consolidação de documentos.

### `ocrmypdf`

O `ocrmypdf` é uma ferramenta de linha de comando que pega um `PDF`, aplica `OCR` nas páginas que estão como imagem ou digitalização, e gera um novo `PDF` pesquisável, normalmente preservando o visual original. Na prática, ele usa motores como `tesseract` por baixo, insere uma camada de texto reconhecido sobre as páginas e facilita muito extrair conteúdo de apostilas, _scans_ e _slides_ sem precisar fazer `OCR` manual página por página. 

**ATENÇÃO**: Você pode utilizar o `pdftotext` e/ou o `tesseract` em arquivos `.pdf` para converter em `.txt` e depois traduzir para o português brasileiro com os comandos do `translate-shell` que serão apresentados depois do passo a passo de como instalar o `translate-shell`.


## 1. Como configurar/instalar/usar o `tesseract OCR` no `Linux Ubuntu` [1][3]

Para configurar/instalar/usar o `tesseract OCR` no `Linux Ubuntu`, você pode seguir estes passos:

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```    

2. Certifique-se de que seu sistema esteja limpo e atualizado.

    2.1 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando:
    
    ```bash
    sudo apt clean
    ``` 
    
    2.2 Remover pacotes `.deb` antigos ou duplicados do `cache` local. É útil para liberar espaço, pois remove apenas os pacotes que não podem mais ser baixados (ou seja, versões antigas de pacotes que foram atualizados). Digite o seguinte comando:
    
    ```bash
    sudo apt autoclean
    ```

    2.3 Remover pacotes que foram automaticamente instalados para satisfazer as dependências de outros pacotes e que não são mais necessários. Digite o seguinte comando:
    
    ```bash
    sudo apt autoremove -y
    ```

    2.4 Buscar as atualizações disponíveis para os pacotes que estão instalados em seu sistema. Digite o seguinte comando e pressione `Enter`: 
    
    ```bash
    sudo apt update
    ```

    2.5 **Corrigir pacotes quebrados**: Isso atualizará a lista de pacotes disponíveis e tentará corrigir pacotes quebrados ou com dependências ausentes:
    
    ```bash
    sudo apt --fix-broken install
    ```

    2.6 Limpar o `cache` do gerenciador de pacotes `apt`. Especificamente, ele remove todos os arquivos de pacotes (`.deb`) baixados pelo `apt` e armazenados em `/var/cache/apt/archives/`. Digite o seguinte comando:
    
    ```bash
    sudo apt clean
    ``` 
    
    2.7 Para ver a lista de pacotes a serem atualizados, digite o seguinte comando e pressione `Enter`:  
    
    ```bash
    sudo apt list --upgradable
    ```

    2.8 Realmente atualizar os pacotes instalados para as suas versões mais recentes, com base na última vez que você executou `sudo apt update`. Digite o seguinte comando e pressione `Enter`:
    
    ```bash
    sudo apt full-upgrade -y
    ```

3. **Instalar o `tesseract OCR`:** Primeiro, você precisa instalar o `tesseract OCR` no seu sistema `Linux`. Isso pode ser feito usando o gerenciador de pacotes da sua distribuição. Por exemplo, no `Ubuntu`, você usaria o seguinte comando no `Terminal Emulator`:

    ```bash
    sudo apt install tesseract-ocr tesseract-ocr-por poppler-utils -y
    ```

4. **Instalar uma Interface Gráfica para `gImageReader` (Obrigatório):** Para instalar a interface gráfica, pode instalar o gImageReader, que é uma interface gráfica para o `tesseract OCR`. Digite o seguinte comando:

    ```bash
    sudo apt install gimagereader -y
    ```

Lembre-se de que a qualidade do `OCR` depende da clareza do texto no `.pdf` original. Textos manuscritos ou com muita formatação gráfica podem não ser reconhecidos com precisão.

### 1.1 Instalar outros idiomas

### 1.1.1 Instalar o idioma português

Para instalar o suporte ao idioma, por exemplo, português no `gImageReader` para reconhecimento OCR, você precisa instalar o pacote de idioma específico do `gImageReader` para português. Aqui estão as etapas que você deve seguir no `Linux Ubuntu`:

1. **Abra o `Terminal Emulator`**: Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```

2. **Instale o Pacote de Idioma `Português` do `gImageReader`:** No `Terminal Emulator`, use o gerenciador de pacotes da sua distribuição para instalar o pacote de idioma. Por exemplo, no `Linux Ubuntu` ou em sistemas baseados no `Debian`, você usaria o seguinte comando:

    ```bash
    sudo apt install tesseract-ocr-por -y
    ```

3. **Verifique a Instalação:** Para verificar se o pacote foi instalado corretamente, você pode listar os idiomas disponíveis do `gImageReader` com o comando: `tesseract --list-langs`

    Você deve ver `por` listado entre os idiomas disponíveis.

4. **Usar o Idioma português no `gImageReader`:** 

    4.1 Abra o `gImageReader`.

    4.2 Carregue o documento `.pdf` ou a imagem que deseja processar.
    
    4.3 Antes de iniciar o reconhecimento OCR, escolha:
    
    4.3.1 A opção `plain text` (esta opção gera um arquivo de texto `.txt`) ou `hOCR` (esta opção gera um arquivo `.pdf` ou `.HMTL`);

    4.3.2 `português` como o idioma de  reconhecimento. Isso geralmente é feito em um menu suspenso ou uma caixa de diálogo de configurações que aparece antes de iniciar o OCR.
    
    4.4 Prossiga com o reconhecimento OCR como faria normalmente.

5. **Salvar o Documento:** Após o reconhecimento OCR, você pode salvar o documento. No caso de querer salvar como `.pdf` pesquisável, procure pela opção 'Salvar' ou 'Exportar como `.pdf`' nas opções de menu do `gImageReader`.


### 1.1.2 Instalar o idioma russo

Para instalar o suporte ao idioma, por exemplo, russo no `gImageReader` para reconhecimento OCR, você precisa instalar o pacote de idioma específico do `gImageReader` para russo. Aqui estão as etapas que você deve seguir no `Linux Ubuntu`:

1. **Abra o `Terminal Emulator`:** Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```

2. **Instale o Pacote de Idioma `Russo` do `gImageReader`:** No `Terminal Emulator`, use o gerenciador de pacotes da sua distribuição para instalar o pacote de idioma. Por exemplo, no `Linux Ubuntu` ou em sistemas baseados no `Debian`, você usaria o seguinte comando:

    ```bash
    sudo apt install tesseract-ocr-rus -y
    ```

3. **Verifique a Instalação:** Para verificar se o pacote foi instalado corretamente, você pode listar os idiomas disponíveis do `gImageReader` com o comando: ``tesseract` --list-langs`

    Você deve ver `rus` listado entre os idiomas disponíveis.

4. **Usar o Idioma `Russo` no `gImageReader`:** 

    4.1 Abra o `gImageReader`.

    4.2 Carregue o documento `.pdf` ou a imagem que deseja processar.
    
    4.3.1 A opção `plain text` (esta opção gera um arquivo de texto `.txt`) ou `hOCR` (esta opção gera um arquivo `.pdf` ou `.HMTL`);

    4.3.2 `russo` como o idioma de  reconhecimento. Isso geralmente é feito em um menu suspenso ou uma caixa de diálogo de configurações que aparece antes de iniciar o OCR.
    
    4.4 Prossiga com o reconhecimento OCR como faria normalmente.

5. **Salvar o Documento:** Após o reconhecimento OCR, você pode salvar o documento. No caso de querer salvar como `.pdf` pesquisável, procure pela opção 'Salvar' ou 'Exportar como `.pdf`' nas opções de menu do `gImageReader`.

### 1.2 Código completo para configurar/instalar/usar

Para configurar/instalar/usar o `gImageReader` no `Linux Ubuntu` sem precisar digitar linha por linha, você pode seguir estas etapas:

1. Abrir o `Terminal Emulator`. Você pode fazer isso pressionando:

    ```bash
    Ctrl + Alt + T
    ```

2. Digite o seguinte comando e pressione `Enter`:

    ```bash
    sudo apt clean
    sudo apt autoclean
    sudo apt autoremove -y
    sudo apt update
    sudo apt --fix-broken install
    sudo apt clean
    sudo apt list --upgradable
    sudo apt full-upgrade -y
    sudo apt install tesseract-ocr -y
    sudo apt install gimagereader -y
    sudo apt install tesseract-ocr-por -y
    sudo apt install tesseract-ocr-rus -y
    ```
    

## 2. Usar o `tesseract OCR` a partir do `Terminal Emulator`

### 2.1 Converter um arquivo `.pdf` para `Plain Text`

  Para converter um arquivo `.pdf` para texto plano (`Plain Text`) usando o `tesseract OCR` pelo `Terminal Emulator` do Linux, você precisará seguir alguns passos, pois o `tesseract` não processa diretamente arquivos `.pdf`. Em vez disso, ele funciona com imagens. Portanto, você terá que converter seu `.pdf` para um formato de imagem antes de usar o `tesseract` para extrair o texto. Aqui está o procedimento geral:

1. **Converter o `.pdf` para Imagens:** Você pode usar a ferramenta `pdftoppm` para converter as páginas do `.pdf` em imagens `.png` ou `.jpeg`. Aqui está um exemplo de como fazer isso para o formato `.png`:

    ```bash
    pdftoppm -r 300 -png arquivo.pdf pagina
    ```

    Isso criará uma série de arquivos de imagem nomeados `"pagina-1.png"`, `"pagina-2.png"` etc., cada um correspondendo a uma página do seu `.pdf`.

2. **Usar o `tesseract` para Converter Imagens em Texto em um idioma específico:** Em seguida, execute o `tesseract` em cada uma das imagens para extrair o texto. Você pode fazer um script simples para automatizar isso se tiver muitas páginas:

    ```bash
    for img in pagina*.png; do
      tesseract "$img" "${img%.*}"
    done
    ```

    Isso irá gerar um arquivo de texto para cada imagem, removendo a extensão do arquivo de imagem e substituindo-a pela extensão `.txt`.

3. **Concatenar os Resultados (Opcional):** Se você quiser ter todo o texto em um único arquivo, pode concatenar todos os arquivos de texto em um só:

    ```bash
    for file in pagina*.txt; do
      cat "$file" >> texto_completo.txt
      echo "Adicionando $file to texto_completo.txt"
    done
    ```

    Isso irá combinar todos os arquivos de texto individuais em um arquivo chamado `"texto_completo.txt"`.

4. **Exclui os arquivos `pagina*` (Opcional):** Se você quiser remover os arquivos, tendo em vista que, finalizou o processo pretendido, execute o seguinte comando dentro da pasta:  `rm -rf pagina_${nome_base}*`

Isso deve permitir que você converta um arquivo `.pdf` em texto usando o `Terminal Emulator` do `Linux`.

### 2.1.1 Converter um arquivo `.pdf` para `Plain Text` para um idioma específico

Para converter um arquivo `.pdf` para texto plano (`Plain Text`) usando o `tesseract` OCR pelo `Terminal Emulator` do Linux, você precisará seguir alguns passos, pois o `tesseract` não processa diretamente arquivos `.pdf`. Em vez disso, ele funciona com imagens. Portanto, você terá que converter seu `.pdf` para um formato de imagem antes de usar o `tesseract` para extrair o texto. Aqui está o procedimento geral:

1. **Converter o `.pdf` para Imagens:** Você pode usar a ferramenta `pdftoppm` para converter as páginas do `.pdf` em imagens `.png` ou `.jpeg`. Aqui está um exemplo de como fazer isso para o formato `.png`:

    ```bash
    pdftoppm -r 300 -png arquivo.pdf pagina
    ```

    Isso criará uma série de arquivos de imagem nomeados `"pagina-1.png"`, `"pagina-2.png"` etc., cada um correspondendo a uma página do seu `.pdf`.

2. **Usar o `tesseract` para Converter Imagens em Texto:** Em seguida, execute o `tesseract` em cada uma das imagens para extrair o texto com o acréscimo do comando `-l rus`. Você pode fazer um script simples para automatizar isso se tiver muitas páginas:

    ```bash
    for img in pagina*.png; do
      tesseract "$img" "${img%.*}" -l rus
    done
    ```

    Isso irá gerar um arquivo de texto para cada imagem, removendo a extensão do arquivo de imagem e substituindo-a pela extensão `.txt`.

3. **Concatenar os Resultados (Opcional):** Se você quiser ter todo o texto em um único arquivo, pode concatenar todos os arquivos de texto em um só:

    ```bash
    for file in pagina*.txt; do
      cat "$file" >> texto_completo.txt
      echo "Adicionando $file to texto_completo.txt"
    done
    ```

    Isso irá combinar todos os arquivos de texto individuais em um arquivo chamado `"texto_completo.txt"`.

4. **Exclui os arquivos `pagina*` (Opcional):** Se você quiser remover os arquivos, tendo em vista que, finalizou o processo pretendido, execute o seguinte comando dentro da pasta:

    ```bash
    rm -rf pagina_${nome_base}*
    ```

Isso deve permitir que você converta um arquivo `.pdf` em texto usando o `Terminal Emulator` do `Linux`.

### 2.1.1 Converter um arquivo `.pdf` para `Plain Text` para um idioma específico e remover as quebras de linhas entre os parágrafos

Para remover as quebras de linha dentro dos parágrafos mantendo-as entre parágrafos distintos, você precisa de uma maneira de diferenciar as quebras de linha que finalizam parágrafos daquelas que são usadas para a formatação de linhas. Geralmente, uma quebra de linha que indica o fim de um parágrafo é seguida por outra quebra de linha (ou seja, uma linha em branco), enquanto que quebras de linha dentro de um parágrafo são únicas.

Você pode ajustar o _script_ para concatenar as linhas de cada arquivo tratando diferentemente esses dois tipos de quebras de linha. No contexto dos arquivos de texto gerados pelo Tesseract, vamos supor que um parágrafo seja definido como um bloco de texto seguido por uma ou mais linhas em branco. Abaixo está um exemplo de _script_ que remove quebras de linha dentro de parágrafos, mas as mantém entre parágrafos:

1. **Defina o nome do arquivo**:

    ```bash
    nome_do_arquivo="nome_do_arquivo.pdf"
    ```

2. **Defina o(s) idioma(s)**: `eng` para inglês, `por` para português, `rus` para russo, `eng+rus` para inglês e russo etc.:

    ```bash
    idioma_ocr="rus"
    ```

    - **`eng`**: especifica que o documento está em inglês

    - **`por`**: especifica que o documento está em português
    
    - **`rus`**: especifica que o documento está em russo (costuma dar problemas, por conta do alfabeto cirílico)
    
    - **`eng+rus`**: especifica que o documento está em inglês e em russo (costuma dar problemas, por conta do alfabeto cirílico)

3. **Extrai o nome base do arquivo sem a extensão `.pdf`** impa ou cria o arquivo antes de começar a adicionar conteúdo:

    ```bash
    nome_base="${nome_do_arquivo%.pdf}"
    ```

4. **Limpa ou cria o arquivo texto_completo.txt com o novo nome base**:

    ```bash
    nome_txt="${nome_base}.txt"
    ```

5. **Converta o PDF para imagens PNG com o prefixo 'pagina_<nome_base>'**: Você pode usar a ferramenta `pdftoppm` para converter as páginas do `.pdf` em imagens `.png` ou `.jpeg`. Aqui está um exemplo de como fazer isso para o formato `.png`:

    ```bash
    pdftoppm -r 300 -png "$nome_do_arquivo" "pagina_${nome_base}_"
    ```

    Isso criará uma série de arquivos de imagem nomeados `"pagina-1_<nome_base>.png"`, `"pagina-2_<nome_base>.png"` etc., cada um correspondendo a uma página do seu `.pdf`.

6. **Usar o `tesseract` para Converter Imagens em PDFs com Texto Selecionável:** Em seguida, modifique o comando do `tesseract` para gerar PDFs em vez de arquivos de texto. Importante adicionar a opção `-l` por se o documento estiver em inglês, ou ajustar para o idioma apropriado do documento:

    ```bash
    for img in pagina_${nome_base}_*.png; do
      tesseract "$img" "${img%.*}" -l $idioma_ocr pdf
      tesseract "$img" "${img%.*}" -l $idioma_ocr > "${img%.*}.txt"
    done
    ```

    Cada comando `tesseract` agora gera um arquivo `.pdf` para cada imagem, com o texto reconhecido embutido como texto selecionável.

7. **Criar um arquivo de texto vazio chamado `texto_completo.txt`:**  comando `echo -n "" > "$nome_txt"` é usado para criar um arquivo de texto vazio chamado `"$nome_txt"` ou para limpar o conteúdo do arquivo se ele já existir sem adicionar uma nova linha:

    ```bash
    "$nome_txt"
    ```

    Vamos quebrar o comando para entender cada parte:

  - **`echo`**: é um comando utilizado para exibir uma linha de texto/string.

  - **`-n`**: é uma opção do comando echo que impede a adição de uma nova linha no final da saída. Normalmente, echo adiciona uma nova linha após o texto exibido, mas `-n` evita isso.

  - **`""`**: representa uma string vazia. Como não há nada entre as aspas, nada será adicionado ao arquivo.

  - **`>`**: é um operador de redirecionamento. Ele direciona a saída de um comando (neste caso, a saída do echo, que é uma string vazia) para um arquivo. Se o arquivo especificado (neste caso, texto_completo.txt) já existir, seu conteúdo será sobrescrito. Se não existir, o arquivo será criado.

8. **Concatenar os Resultados (Opcional):** Se você quiser ter todo o texto em um único arquivo, pode concatenar todos os arquivos de texto em um só:

    ```bash
    for file in pagina_${nome_base}_*.txt; do
      # Este comando utiliza awk para preservar quebras de linha entre parágrafos.
      # O RS (Record Separator) é uma string vazia, o que faz o awk tratar parágrafos como registros.
      # O ORS (Output Record Separator) define uma quebra de linha dupla como separador de registros na saída,
      # e o FS (Field Separator) define uma quebra de linha como separador de campos dentro dos registros.
      awk 'BEGIN{RS="";ORS="\n\n";FS="\n"} {$1=$1; print}' "$file" >> "$nome_txt"
      echo "Adicionando $file a $nome_txt"
    done
    ```

    Isso irá combinar todos os arquivos de texto individuais em um arquivo chamado `"texto_completo.txt"`.

9. **Exclui os arquivos `pagina*` (Opcional):** Se você quiser remover os arquivos, tendo em vista que, finalizou o processo pretendido, execute o seguinte comando dentro da pasta:

    ```bash
    rm -rf pagina_${nome_base}*
    ```

    Isso deve permitir que você converta um arquivo `.pdf` em texto usando o `Terminal Emulator` do `Linux`.

### 2.1.2 Converter um arquivo `.pdf` **NÃO** selecionável para `.pdf` selecionável em um idioma específico

Para converter um arquivo `.pdf` para texto plano (Plain Text) usando o `tesseract` OCR pelo `Terminal Emulator` do Linux, você precisará seguir alguns passos, pois o `tesseract` não processa diretamente arquivos `.pdf`. Em vez disso, ele funciona com imagens. Portanto, você terá que converter seu `.pdf` para um formato de imagem antes de usar o `tesseract` para extrair o texto. Aqui está o procedimento geral:

1. **Defina o nome do arquivo**:

    ```bash
    nome_do_arquivo="nome_do_arquivo.pdf"
    ```

2. **Defina o(s) idioma(s)**: `eng` para inglês, `por` para português, `rus` para russo, `eng+rus` para inglês e russo etc.:

    ```bash
    idioma_ocr="rus"
    ```

    - **`eng`**: especifica que o documento está em inglês
    
    - **`por`**: especifica que o documento está em português
    
    - **`rus`**: especifica que o documento está em russo (costuma dar problemas, por conta do alfabeto cirílico)
    
    - **`eng+rus`**: especifica que o documento está em inglês e em russo (costuma dar problemas, por conta do alfabeto cirílico)

3. **Extrai o nome base do arquivo sem a extensão `.pdf`** impa ou cria o arquivo antes de começar a adicionar conteúdo:

    ```bash
    nome_base="${nome_do_arquivo%.pdf}"
    ```

4. **Limpa ou cria o arquivo texto_completo.txt com o novo nome base**:

    ```bash
    nome_txt="${nome_base}.txt"
    ```

5. **Converta o PDF para imagens PNG com o prefixo 'pagina_<nome_base>'**: Você pode usar a ferramenta `pdftoppm` para converter as páginas do `.pdf` em imagens `.png` ou `.jpeg`. Aqui está um exemplo de como fazer isso para o formato `.png`:

    ```bash
    pdftoppm -r 300 -png "$nome_do_arquivo" "pagina_${nome_base}_"
    ```

    Isso criará uma série de arquivos de imagem nomeados `"pagina-1_<nome_base>.png"`, `"pagina-2_<nome_base>.png"` etc., cada um correspondendo a uma página do seu `.pdf`.

6. **Usar o `tesseract` para Converter Imagens em PDFs com Texto Selecionável:** Em seguida, modifique o comando do `tesseract` para gerar PDFs e arquivos de texto. Importante adicionar a opção `-l` por se o documento estiver em inglês, ou ajustar para o idioma apropriado do documento:

    ```bash
    # Limpa ou cria o arquivo texto_completo.txt antes de começar a adicionar conteúdo
    echo -n "" > "$nome_txt"

    # Processa cada imagem, gerando um PDF e um arquivo de texto correspondente
    for img in pagina_${nome_base}_*.png; do
        tesseract "$img" "${img%.*}" -l $idioma_ocr pdf
        tesseract "$img" "${img%.*}" -l $idioma_ocr txt > "${img%.*}.txt"
        cat "${img%.*}.txt" >> "$nome_txt"
        echo "Adicionando ${img%.*}.txt a $nome_txt"
    done
    ```

    Cada comando `tesseract` agora gera um arquivo `.pdf` e `.txt` para cada imagem, com o texto reconhecido embutido como texto selecionável.

7. **Concatenar os PDFs em um Único Arquivo:** Após gerar os PDFs individuais, você precisará concatená-los em um único arquivo `.pdf`. Uma ferramenta que pode fazer isso é o pdfunite, parte do pacote `poppler-utils`:

    ```bash
    pdfunite pagina_${nome_base}_*.pdf "${nome_base}_completo.pdf"
    ```

    Este comando une todos os PDFs gerados (`pagina-1_<nome_base>.pdf`, `pagina-2_<nome_base>.pdf` etc.) em um novo arquivo `.pdf` chamado `<nome_base>_completo.pdf`.

8. **Exclui os arquivos `pagina*` (Opcional):** Se você quiser remover os arquivos, tendo em vista que, finalizou o processo pretendido, execute o seguinte comando dentro da pasta:

    ```bash
    rm -rf pagina_${nome_base}*
    ```


#### 3. Converter um arquivo `.pdf` **NÃO** selecionável para `.pdf` selecionável em mais de um idioma

Para converter um arquivo `.pdf` para texto plano (Plain Text) usando o `tesseract` OCR pelo `Terminal Emulator` do `Linux Ubuntu`, você precisará seguir alguns passos, pois o `tesseract` não processa diretamente arquivos `.pdf`. Em vez disso, ele funciona com imagens. Portanto, você terá que converter seu `.pdf` para um formato de imagem antes de usar o `tesseract` para extrair o texto. Aqui está o procedimento geral:

1. **Defina o nome do arquivo**:

    ```bash
    nome_do_arquivo="nome_do_arquivo.pdf"
    ```

2. **Defina o(s) idioma(s)**: `eng` para inglês, `por` para português, `rus` para russo, `eng+rus` para inglês e russo etc.:

    ```bash
    idioma_ocr="eng+rus"
    ```

    - **`eng`**: especifica que o documento está em inglês
    
    - **`por`**: especifica que o documento está em português
    
    - **`rus`**: especifica que o documento está em russo (costuma dar problemas, por conta do alfabeto cirílico)
    
    - **`eng+rus`**: especifica que o documento está em inglês e em russo (costuma dar problemas, por conta do alfabeto cirílico)

3. **Extrai o nome base do arquivo sem a extensão `.pdf`** impa ou cria o arquivo antes de começar a adicionar conteúdo:

    ```bash
    nome_base="${nome_do_arquivo%.pdf}"
    ```

4. **Limpa ou cria o arquivo texto_completo.txt com o novo nome base**:s
  
    ```bash
    nome_txt="${nome_base}.txt"
    ```

5. **Converta o PDF para imagens PNG com o prefixo 'pagina_<nome_base>'**: Você pode usar a ferramenta `pdftoppm` para converter as páginas do `.pdf` em imagens `.png` ou `.jpeg`. Aqui está um exemplo de como fazer isso para o formato `.png`:

    ```bash
    pdftoppm -r 300 -png "$nome_do_arquivo" "pagina_${nome_base}_"
    ```

    Isso criará uma série de arquivos de imagem nomeados `"pagina-1_<nome_base>.png"`, `"pagina-2_<nome_base>.png"` etc., cada um correspondendo a uma página do seu `.pdf`.

6. **Usar o `tesseract` para Converter Imagens em PDFs com Texto Selecionável:** Em seguida, modifique o comando do `tesseract` para gerar PDFs e arquivos de texto. Importante adicionar a opção `-l` por se o documento estiver em inglês, ou ajustar para o idioma apropriado do documento:

    ```bash
    # Limpa ou cria o arquivo texto_completo.txt antes de começar a adicionar conteúdo
    echo -n "" > "$nome_txt"

    # Processa cada imagem, gerando um PDF e um arquivo de texto correspondente
    for img in pagina_${nome_base}_*.png; do
        tesseract "$img" "${img%.*}" -l $idioma_ocr pdf
        tesseract "$img" "${img%.*}" -l $idioma_ocr txt > "${img%.*}.txt"
        cat "${img%.*}.txt" >> "$nome_txt"
        echo "Adicionando ${img%.*}.txt a $nome_txt"
    done
    ```

    Cada comando `tesseract` agora gera um arquivo `.pdf` e `.txt` para cada imagem, com o texto reconhecido embutido como texto selecionável.

7. **Concatenar os PDFs em um Único Arquivo:** Após gerar os PDFs individuais, você precisará concatená-los em um único arquivo `.pdf`. Uma ferramenta que pode fazer isso é o pdfunite, parte do pacote `poppler-utils`:

    ```bash
    pdfunite pagina_${nome_base}_*.pdf "${nome_base}_completo.pdf"
    ```

    Este comando une todos os PDFs gerados (`pagina-1_<nome_base>.pdf`, `pagina-2_<nome_base>.pdf` etc.) em um novo arquivo `.pdf` chamado `<nome_base>_completo.pdf`.

8. **Exclui os arquivos `pagina*` (Opcional):** Se você quiser remover os arquivos, tendo em vista que, finalizou o processo pretendido, execute o seguinte comando dentro da pasta:

    ```bash
    rm -rf pagina_${nome_base}*
    ```


### 4. Salvar somentes as imagens de um `.pdf` com o `tesseract`

O `tesseract OCR` é uma ferramenta de reconhecimento óptico de caracteres e não é projetado para extrair ou salvar imagens de documentos `.pdf`. Seu propósito principal é converter imagens que contêm texto em texto editável ou em um formato de documento que mantém o texto reconhecido.

Para extrair imagens de um `.pdf`, você precisaria usar outras ferramentas especificamente destinadas a essa tarefa. Uma das ferramentas mais comuns para manipulação de arquivos `.pdf` em ambientes `Linux Ubuntu` é o `pdfimages`, que faz parte do pacote `poppler-utils`. pdfimages é uma ferramenta de linha de comando que pode ser usada para extrair imagens embutidas em documentos `.pdf`.

## 5. Converter o arquivo `.pdf` selecionável em `.pdf` **NÃO** selecionável 

Aqui está uma abordagem simplificada de como você poderia fazer isso, combinando outras ferramentas com o `Tesseract`, se necessário:

1. **Extrair páginas do PDF como imagens:** Você pode usar o `pdftoppm` (parte do Poppler Utils) para converter cada página do PDF em uma imagem:

    ```bash
    pdftoppm seu_documento.pdf pagina -png
    ```

    Isso criará uma série de arquivos PNG, um para cada página do seu PDF, nomeados `pagina-1.png`, `pagina-2.png` etc.

2. **Recompilar as imagens em um PDF:** Após ter as imagens, você pode usar uma ferramenta como o `img2pdf` para recompilar essas imagens de volta em um único arquivo PDF:

    ```bash
    img2pdf pagina-*.png -o seu_documento_nao_selecionavel.pdf
    ```

    Este método garante que o conteúdo do PDF seja convertido em imagens, tornando o texto não selecionável, mas mantendo o layout original das páginas. A desvantagem é a perda de recursos de texto, como pesquisa e acessibilidade, e potencialmente um aumento no tamanho do arquivo.

3. **Exclui os arquivos `pagina*` (Opcional):** Se você quiser remover os arquivos, tendo em vista que, finalizou o processo pretendido, execute o seguinte comando dentro da pasta:
    
    ```bash
    rm -rf pagina_${nome_base}*
    ```

Lembre-se, o `Tesseract` entra em jogo se você precisar fazer `OCR` nas imagens para extrair texto delas, mas isso contradiz a intenção de tornar o texto não selecionável. Se o objetivo é apenas criar um PDF com texto não selecionável, as etapas acima (sem envolver o `Tesseract`) são suficientes.

## Referências

[1] OPENAI. **Instalar o `tesseract` no `linux ubuntu` pelo `terminal emulator`.** Disponível em: <https://chat.openai.com/c/dc4b629e-7432-44d6-bc0d-7caefcc8e11a> (texto adaptado). ChatGPT. Acessado em: 15/12/2023 12:00.

[2] OPENAI. **Vs code: editor popular.** Disponível em: <https://chat.openai.com/c/b640a25d-f8e3-4922-8a3b-ed74a2657e42> (texto adaptado). ChatGPT. Acessado em: 15/12/2023 12:00.


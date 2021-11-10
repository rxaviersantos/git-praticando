<div align="center"> 
  
  <h1> Git - Conceitos e utilização na prática com GitHub  </h1>
  <img src="https://img.icons8.com/nolan/64/git.png"/>
<img src="https://img.icons8.com/nolan/64/github.png"/>
<img src="https://img.icons8.com/nolan/64/windows-10.png"/>  
  
</div>

# 📜 Documentação

[git-scm.com/book/en/v2](https://git-scm.com/book/en/v2) O livro Pro Git completo.

## Como o Git funciona 
> o Git armazena e pensa sobre as informações de uma maneira muito diferente, e entender essas diferenças ajudará você a evitar ficar confuso ao usá-las.

<div align="center"> 
  
  <h1> 
  <img src="https://user-images.githubusercontent.com/85380530/140005919-8f4ee741-02bf-4f12-8903-138da628e591.jpg"/>
</div>

# Primeiros passos - Configuração inicial do Git
  
## Começando - Instalando o Git  [Installing](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) 
> Instalando Git
  
Antes de começar a usar o Git, você deve disponibilizá-lo em seu computador. Mesmo se já estiver instalado, é provavelmente uma boa ideia atualizar para a versão mais recente. Você pode instalá-lo como um pacote ou por meio de outro instalador, ou baixar o código-fonte e compilá-lo você mesmo.
  
## Instalando no Windows 
  
  Existem também algumas maneiras de instalar o Git no Windows. A compilação mais oficial está disponível para download no site do Git. Basta ir a https://git-scm.com/download/win e o download começará automaticamente. Observe que este é um projeto chamado Git para Windows, que é separado do próprio Git; para obter mais informações sobre ele, vá para https://gitforwindows.org .

Para obter uma instalação automatizada, você pode usar o pacote Git Chocolatey . Observe que o pacote Chocolatey é mantido pela comunidade.
  
 Configurando o git com o seguinte comando `git config` 
  
 ```sh
git config --global user.name "Rodrigo"
``` 
  
Adicionando o endereço de e-mail pelo seguinte comando.
  
 ```sh
git config --global user.email "rodrigomxsantos@gmail.com"
``` 
  

 
Configurando meu editor Visual Studio Code (vscode) como editor git padrão

 ```sh
git config --global core.editor "code --wait"
``` 

## Resultado
  
<img src="https://user-images.githubusercontent.com/85380530/140174705-732910cb-7279-4198-bfbe-5a535bf2ce1d.png" height="300" width="600">


# Obtendo ajuda

Se você precisar de ajuda ao usar o Git, há três maneiras equivalentes de obter ajuda da página de manual (manpage) abrangente para qualquer um dos comandos do Git:
  
  ```sh
  git help <verb>
  git <verb> --help
  man git-<verb>
  ```
Esses comandos são bons porque você pode acessá-los em qualquer lugar, mesmo offline. Se você precisar de ajuda de uma pessoa, você pode tentar o #git, #github, ou #gitlabcanais no servidor Libera bate-papo IRC, que pode ser encontrada em https://libera.chat/ . Esses canais são regularmente preenchidos com centenas de pessoas que têm muito conhecimento sobre o Git e muitas vezes estão dispostas a ajudar.

# Obtendo um Repositório Git

Normalmente, você obtém um repositório Git de duas maneiras:
  
  > 1. Você pode pegar um diretório local que atualmente não está sob controle de versão e transformá-lo em um repositório Git.
  
  > 2. Você pode clonar um repositório Git existente de outro lugar.
  
Em qualquer caso, você acaba com um repositório Git em sua máquina local, pronto para trabalhar.

# Inicializando um Repositório em um Diretório Existente

Se você tem um diretório de projeto que atualmente não está sob controle de versão e deseja começar a controlá-lo com o Git, primeiro você precisa ir para o diretório desse projeto.

No windows:
  
```sh 
cd C:/Users/user/my_project
```
e digite:
```sh 
git init 
```
Isso cria um novo subdiretório chamado .git que contém todos os seus arquivos de repositório necessários - um esqueleto de repositório Git.
Neste ponto, nada em seu projeto foi rastreado ainda. Consulte [ Git Internals](https://git-scm.com/book/en/v2/Git-Internals-Plumbing-and-Porcelain#ch10-git-internals)  para obter mais informações sobre exatamente quais arquivos estão contidos no .gitdiretório que você acabou de criar.
  
# Clonando um Repositório Existente
  
Se você deseja obter uma cópia de um repositório Git existente - por exemplo, um projeto com o qual gostaria de contribuir - o comando que você precisa é ``` git clone```.
Cada versão de cada arquivo para o histórico do projeto é puxada para baixo por padrão quando você executa ```git clone```. Na verdade, se o disco do servidor for corrompido, muitas vezes você pode usar quase qualquer um dos clones em qualquer cliente para definir o servidor de volta ao estado em que estava quando foi clonado (você pode perder alguns ganchos do lado do servidor e tal, mas todos os dados versionados estariam lá - veja Obtendo Git em um servidor para mais detalhes).

Você clona um repositório com o comando.
```sh
git clone <url>
```
O Git tem vários protocolos de transferência diferentes que você pode usar.
O [ obter Git em um servidor ](https://git-scm.com/book/en/v2/Git-on-the-Server-Getting-Git-on-a-Server#_getting_git_on_a_server) apresentará todas as opções disponíveis que o servidor pode configurar para acessar seu repositório Git e os prós e contras de cada uma.

# Gravando Mudanças no Repositório
Normalmente, você deseja começar a fazer alterações e enviar instantâneos dessas alterações em seu repositório cada vez que o projeto atinge um estado que deseja registrar.
Lembre-se que cada arquivo em seu diretório de trabalho pode estar em um dos dois estados: monitorado ou untracked . Os arquivos rastreados são arquivos que estavam no último instantâneo, bem como quaisquer arquivos recém-testados; eles podem ser não modificados, modificados ou encenados. Resumindo, os arquivos rastreados são arquivos que o Git conhece.

Arquivos não rastreados são todo o resto - quaisquer arquivos em seu diretório de trabalho que não estavam em seu último instantâneo e não estão em sua área de teste. Quando você clona um repositório pela primeira vez, todos os seus arquivos serão rastreados e não modificados porque Git acabou de fazer o check-out e você não editou nada.
Conforme você edita arquivos, Git os vê como modificados, porque você os alterou desde seu último commit. Conforme você trabalha, você seleciona esses arquivos modificados e, em seguida, confirma todas as mudanças em estágio, e o ciclo se repete.
  
> O ciclo de vida do status de seus arquivos.

<img src="https://user-images.githubusercontent.com/85380530/140184033-a72a76dd-bb5e-48f8-9905-89385eab728c.png" height="300" width="600">


### Verificando o status dos arquivos

Utilizando o comando ``git status`` para determinar quais arquivos estão em qual estado.

```sh
git status
```
<img src="https://user-images.githubusercontent.com/85380530/140184937-4932362f-87e5-4e02-9988-057464767791.png" height="300" width="600">

  
Isso significa que meu diretório de trabalho está limpo; em outras palavras, nenhum de seus arquivos rastreados é modificado. O Git também não vê nenhum arquivo não rastreado, ou eles estariam listados aqui. Finalmente, o comando informa em qual branch você está e informa que ele não divergiu do mesmo branch no servidor. 
Por enquanto, essa branch é sempre main, que é a minha branch padrão.
  
Digamos que você adicione um novo arquivo ao seu projeto, um mapaGit.md arquivo simples . Se o arquivo não existia antes e você executá-lo ``git status``, verá o arquivo não rastreado assim:  

Arquivos do projeto 
  
<img src="https://user-images.githubusercontent.com/85380530/140213253-0ca7ed71-738e-4b7c-ad57-37e1f32c57ff.png" height="300" width="600">

Adicionando um novo arquivo mapaGit

<img src="https://user-images.githubusercontent.com/85380530/140231553-24f6e66f-ee9d-4039-bbc4-9e54f7eb2217.png" height="300" width="600">
  
Resultado do comando `` git status`` 
  
<img src="https://user-images.githubusercontent.com/85380530/140234086-bf3e9451-eea2-41e9-8cbc-36a062be9b7e.png" height="300" width="600">
  
Adicionando novos arquivos

<img src="https://user-images.githubusercontent.com/85380530/140977493-42b85e69-fe3b-44ee-a8d4-bf3e2d12fd3c.png" height="300" width="600">

  
Você pode ver que meu novo mapaGit arquivo não está rastreado, porque está sob o título “Arquivos não rastreados” em sua saída de status. Untracked basicamente significa que o Git vê um arquivo que você não tinha no snapshot anterior (commit) e que ainda não foi testado; O Git não começará a incluí-lo em seus instantâneos de commit até que você diga explicitamente para fazer isso.
  
### Rastreando Novos Arquivos
  
Rastreando meus novos arquivos, usando o comando git add. Para começar a rastrear os arquivos mapaGit e README , você pode executar o seguinte:
  
```sh
git add mapGit
git add README
```
Executando o comando ``git status`` novamente, poderá ver que os arquivos agora está rastreado e preparado para ser confirmado.
  
<img src="https://user-images.githubusercontent.com/85380530/140980667-877bcd54-6382-46fd-8105-f7badf8e607e.png" height="300" width="600">
  
Você pode dizer que está encenado porque está sob o título “Alterações a serem confirmadas”. Se você confirmar neste ponto, a versão do arquivo no momento em que você executou ``git add`` é o que estará no instantâneo histórico subsequente. Você deve se lembrar que quando executou ``git init`` antes, você então executou ``git add <files>`` isso era para começar a rastrear arquivos em seu diretório. O ``git add`` comando usa um nome de caminho para um arquivo ou diretório; se for um diretório, o comando adiciona todos os arquivos nesse diretório recursivamente.

### Arquivos modificados de teste

Alterando o arquivo README rastreado anteriormente inserindo o texto CONTRIBUINDO.md, em seguida, executando o comando ``git staus`` novamente.
  
<img src="https://user-images.githubusercontent.com/85380530/140988442-6e5de222-250d-4f2d-b7f8-ff92a9d92c2f.png" height="300" width="600">
  
O arquivo CONTRIBUINDO.md aparece em uma seção chamada “Alterações não testadas para confirmação” - o que significa que um arquivo rastreado foi modificado no diretório de trabalho, mas ainda não testado. Para prepará-lo, vou executar o ``git add`` comando, em seguida, executar ``git`` status novamente:
  
### Status curto

O Git também possui um sinalizador de status curto para que você possa ver suas alterações de uma forma mais compacta. Se você executar ``git status -s`` ou ``git status --short `` irá obter uma saída muito mais simplificada do comando:
  
```sh
git status -s
git status --short
```
<img src="https://user-images.githubusercontent.com/85380530/140992673-cea8e65c-20e2-40ed-817c-4fb9abc9732f.png" height="250" width="600">
  
Os novos arquivos que não são rastreados têm um ?? próximo a eles, os novos arquivos que foram adicionados à área de teste têm um A, os arquivos modificados têm um M e assim por diante.

### Ignorando arquivos
  
Freqüentemente, você terá uma classe de arquivos que não deseja que o Git adicione automaticamente ou até mesmo mostre que não foram rastreados. Geralmente, são arquivos gerados automaticamente, como arquivos de log ou arquivos produzidos por seu sistema de compilação.
  
 Aqui está um .gitignorearquivo de exemplo :
  
```sh
cat .gitignore
*.[oa]
*~
```
> A primeira linha diz ao Git para ignorar todos os arquivos que terminam em “.o” ou “.a” - objetos e arquivos compactados que podem ser o produto da construção de seu código.
> A segunda linha diz ao Git para ignorar todos os arquivos cujos nomes terminam com um til ( ~), que é usado por muitos editores de texto como o Emacs para marcar arquivos temporários.
> Você também pode incluir um diretório log, tmp ou pid; documentação gerada automaticamente; e assim por diante.

As regras para os padrões que você pode colocar no ``.gitignore`` arquivo são as seguintes:
 
 - Linhas em branco ou linhas que começam com #são ignoradas.
 - Os padrões glob padrão funcionam e serão aplicados recursivamente em toda a árvore de trabalho.
 - Você pode iniciar os padrões com uma barra ( /) para evitar a recursividade.
 - Você pode encerrar os padrões com uma barra ( /) para especificar um diretório.
 - Você pode negar um padrão iniciando-o com um ponto de exclamação ( !).

Os padrões Glob são como expressões regulares simplificadas que os shells usam.
  
- Um asterisco ( *) corresponde a zero ou mais caracteres; 
- [abc] corresponde a qualquer caractere dentro dos colchetes (neste caso, a, b ou c);
- um ponto de interrogação ( ?) corresponde a um único caractere;
- Colchetes envolvendo caracteres separados por um hífen ( [0-9]) correspondem a qualquer caractere entre eles (neste caso, de 0 a 9). 
- Você também pode usar dois asteriscos para corresponder a diretórios aninhados; a/**/ziria corresponder a/z, a/b/z, a/b/c/z, e assim por diante.
  
Aqui está outro ``.gitignore`` arquivo de exemplo :

```sh
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf files in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```

### Visualizando Suas Mudanças Estagiadas e Não Estagiadas

Você deseja saber exatamente o que alterou, não apenas quais arquivos foram alterados - você pode usar o ``git diff`` comando. Abordaremos ``git diff`` com mais detalhes posteriormente, mas provavelmente você o usará com mais frequência para responder a estas duas perguntas: O que você mudou, mas ainda não testou? E o que você encenou que está prestes a cometer? Embora ``git status`` responda a essas perguntas de maneira geral listando os nomes dos arquivos, ``git diff`` mostra as linhas exatas adicionadas e removidas - o patch, por assim dizer.
  
Editando o README arquivo novamnete e visualizando através do comando ``git status``.
  
<img src="https://user-images.githubusercontent.com/85380530/141041858-84c220c5-97ce-405c-9755-86e9fdffccf4.png" height="300" width="600">
  
Visualizando a alteração através do comando ``git diff``.
  
<img src="https://user-images.githubusercontent.com/85380530/141042166-a9deb410-ba11-4d3d-b3a6-90e17dcfa001.png" height="300" width="600">
  
O comando ``git diff`` por si só não mostra todas as mudanças feitas desde seu último commit - apenas as mudanças que ainda não foram testadas. Se você testou todas as suas alterações, ``git diff`` não fornecerá saída.
  
Utilizando o comando ``git diff --cached`` para ver o que foi testado.

<img src="https://user-images.githubusercontent.com/85380530/141042943-b309adca-467b-4686-bf43-0d38b145e2c7.png" height="300" width="600">
  
### Comprometendo suas mudanças
  
Lembre-se de que tudo o que ainda não foi testado - quaisquer arquivo criado ou modificado e que não executou ``git add`` desde que os editei não entrará neste commit. Eles permanecerão como arquivos modificados em seu disco. Nesse caso, digamos que da última vez que executei o comando git status, vi que tudo foi testado, então você está pronto para confirmar estas alterações. A maneira mais simples de confirmar é digitar ``git commit``:
  
```sh
git commit 
```
Este comando irá iniciar meu editor de escolha e exibir a seguinte mensagem:
  
<img src="https://user-images.githubusercontent.com/85380530/141044464-24c7f0cc-d284-4a2e-b78f-c8e969c25c03.png" height="300" width="600">
  
Esta é uma mensagem de confirmação padrão contém a saída mais recente do ``git status`` comando comentado e uma linha vazia no topo. Você pode remover esses comentários e digitar sua mensagem de commit, ou você pode deixá-los lá para ajudá-lo a lembrar o que está cometendo.
  

Quando saio do editor, Git cria meu ``commit`` com aquela mensagem de commit (com os comentários e diff retirados).

Como alternativa, vou digitar minha mensagem de confirmação inline com o ``commit`` comando, especificando-a após um ``-m`` sinalizador, como este:

```sh
$ git commit -m "corrigir benchmarks"
```
<img src="https://user-images.githubusercontent.com/85380530/141045530-94ec9fb1-bd5e-4fba-8215-07bb46b46046.png" height="300" width="600">

Criado meu primeiro commit lembre-se de que o commit registra o snapshot que você configurou em sua área de teste. Qualquer coisa que você não encenou ainda está lá, modificada; você pode fazer outro commit para adicioná-lo ao seu histórico. Cada vez que você executa um commit, você está gravando um instantâneo do seu projeto que você pode reverter ou comparar mais tarde.
  
### Removendo arquivos
  
O ``git rm`` comando remove o arquivo de seu diretório de trabalho para que você não o veja como um arquivo não rastreado da próxima vez.
  
Excutando o comando ``git rm`` ele iniciará a remoção do arquivo:
  
```sh
git rm
```
<img src="https://user-images.githubusercontent.com/85380530/141046752-71e29b8d-7430-411a-a34c-03200f390983.png" height="300" width="600">
  
Outra coisa útil que você pode querer fazer é manter o arquivo em sua árvore de trabalho, mas removê-lo de sua área de teste. Em outras palavras, você pode querer manter o arquivo em seu disco rígido, mas não deixar que o Git o rastreie mais. Isso é particularmente útil se você se esqueceu de adicionar algo ao ``.gitignore`` arquivo e o preparou acidentalmente, como um grande arquivo de log ou um monte de ``.a`` arquivos compilados. Para fazer isso, use a ``--cached`` opção:

```sh
$ git rm --cached README
```
Passando os arquivos, diretórios e padrões de arquivos globais para o git rmcomando. Isso significa que você pode fazer coisas como:

```sh
$ git rm log/\*.log
```
A barra invertida ``( \)`` na frente do ``*.`` Isso é necessário porque o Git faz sua própria expansão de nome de arquivo, além da expansão de nome de arquivo do shell. Este comando remove todos os arquivos que possuem a ``.log`` extensão no ``log``/diretório. Ou você pode fazer algo assim:

```sh 
$ git rm \*~
```
### Movendo arquivos
  
Renomeando um arquivo no Git, você pode executar algo como:
  
```sh
git mv file_from file_to
```
Executando e observando o status, verá que o Git o considera um arquivo renomeado:

```sh 
$ git mv README.md README
```
<img src="https://user-images.githubusercontent.com/85380530/141048744-abc2f25b-cfc9-489c-bec0-e0ed5703404c.png" height="300" width="600">
  
No entanto, isso é equivalente a executar algo assim:

```sh 
$ mv README.md README
$ git rm README.md
$ git add README
```
Não importa se você renomeia um arquivo dessa maneira ou com o mvcomando. A única diferença real é que ``git mv`` é um comando em vez de três é uma função de conveniência. Mais importante, você pode usar qualquer ferramenta que desejar para renomear um arquivo e endereçar o add / rm mais tarde, antes de confirmar.

 


  
  
  
  
  
🚧 Em construção 🚧  
  
  





  



  
  
  
  
  
  

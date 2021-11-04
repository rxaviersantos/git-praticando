<div align="center"> 
  
  <h1> Git - Conceitos e utilização na prática com GitHub  </h1>
  <img src="https://img.icons8.com/nolan/64/git.png"/>
<img src="https://img.icons8.com/nolan/64/github.png"/>
<img src="https://img.icons8.com/nolan/64/windows-10.png"/>  
  
</div>

# 📜 Documentation 

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


Verificando o status de seus arquivos com o comando:

A principal ferramenta que você usa para determinar quais arquivos estão em qual estado é o ``git status`` comando.

```sh
git status
```
<img src="https://user-images.githubusercontent.com/85380530/140184937-4932362f-87e5-4e02-9988-057464767791.png" height="300" width="600">

  
Isso significa que você tem um diretório de trabalho limpo; em outras palavras, nenhum de seus arquivos rastreados é modificado. O Git também não vê nenhum arquivo não rastreado, ou eles estariam listados aqui. Finalmente, o comando informa em qual branch você está e informa que ele não divergiu do mesmo branch no servidor. 
Por enquanto, essa branch é sempre main, que é a minha branch padrão.
  
Digamos que você adicione um novo arquivo ao seu projeto, um mapagit.md arquivo simples . Se o arquivo não existia antes e você executá-lo ``git status``, verá o arquivo não rastreado assim:  

Arquivos do projeto 
  
<img src="https://user-images.githubusercontent.com/85380530/140213253-0ca7ed71-738e-4b7c-ad57-37e1f32c57ff.png" height="300" width="600">

Adicionando um novo arquivo ao projeto

<img src="https://user-images.githubusercontent.com/85380530/140231553-24f6e66f-ee9d-4039-bbc4-9e54f7eb2217.png" height="300" width="600">
  
Resultado do comando `` git status`` 
  
<img src="https://user-images.githubusercontent.com/85380530/140234086-bf3e9451-eea2-41e9-8cbc-36a062be9b7e.png" height="300" width="600">
  
Você pode ver que seu novo mapagit arquivo não está rastreado, porque está sob o título “Arquivos não rastreados” em sua saída de status. Untracked basicamente significa que o Git vê um arquivo que você não tinha no snapshot anterior (commit) e que ainda não foi testado; O Git não começará a incluí-lo em seus instantâneos de commit até que você diga explicitamente para fazer isso. Ele faz isso para que você não comece a incluir acidentalmente arquivos binários gerados ou outros arquivos que você não pretendia incluir. Você quer começar a incluir mapagit, então vamos começar a rastrear o arquivo.
  
Rastreando Novos Arquivos
  
Para começar a rastrear um novo arquivo, você usa o comando git add. Para começar a rastrear o MAPAGIT arquivo, você pode executar o seguinte:
  
```sh
git add mapagit
```
Se você executar o comando de ``git status`` novamente, poderá ver que o mapagit arquivo agora está rastreado e preparado para ser confirmado:  
  
<img src="https://user-images.githubusercontent.com/85380530/140234993-86407e19-9775-4045-8c98-d00c73b4968b.png" height="300" width="600">
  
Você pode dizer que está encenado porque está sob o título “Alterações a serem confirmadas”. Se você confirmar neste ponto, a versão do arquivo no momento em que você executou ``git add`` é o que estará no instantâneo histórico subsequente. Você deve se lembrar que quando executou ``git init`` antes, você então executou ``git add <files>`` isso era para começar a rastrear arquivos em seu diretório. O ``git add`` comando usa um nome de caminho para um arquivo ou diretório; se for um diretório, o comando adiciona todos os arquivos nesse diretório recursivamente.

  
  
🚧 Em construção 🚧  
  
  





  



  
  
  
  
  
  

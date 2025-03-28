---
title: Bem-vindo Neovim
date: 2025-03-27 12:00:00 -0300
categories: [Neovim, Wsl2, Tutorial]
tags: [neovim, wsl2, ubuntu, tutorial]
description: Uma breve explicação sobre Neovim e um guia para você configurar e já utilizar.
---

## Introdução

Na programação temos vários tipos de **editores de textos** e **IDEs**. O Vim é um exemplo de editor de texto.

O Neovim é uma **evolução** significativa do Vim, mantendo sua essência.
E sua configuração saiu do Vimscript para **Lua**, essa **belíssima linguagem brasileira** e muito utilizada em jogos.

Há perguntas muito boas sobre por que não utilizar o Neovim. E vi diversas respostas para esses questionamentos.

* Por que usar Neovim se já utilizo Visual Studio Code, Visual Studio, Rider etc?
* Por que aprender mais uma ferramenta?
* Tem tanta coisa para estudar por que mais isso?

Não acho que minhas respostas para essas perguntas sejam boas, então direi **meus motivos** para **estudar** e **aprender**.

* Usa **Lua**.
* **Muito customizável**, desde aparência até ferramentas auxiliares para desenvolvimento.
* Apostei na **produtividade** prometida.
* Assisti um vídeo do professor **Clóvis de Barros Filho** sobre *brio*. Esse vídeo me motivou muito, recomendo assistir: [Prof. Clóvis de Barros - Brio](https://www.youtube.com/watch?v=TRPBY_lxJfE).
* Ferramenta **veloz** e **leve**.
* **Software livre** e **open-source**.

## Sobre Neovim

O Vim e o Neovim possuem **três modos principais**: **Normal**, **Insert**, **Visual**.

A maioria dos atalhos são intuitivos e geralmente correspondem à primeira letra da ação em inglês.
* `i` = Insert Mode (há outras teclas para trocar pro Insert Mode, por enquanto foca no `i`)
* `v` = Visual Mode
* `ESC` ou `Ctrl+C` = Normal Mode

## Comandos Essenciais

### Básico

* `i` = Insert Mode (há outros comandos para isso que muda o começo de onde será inserido).
* `Esc` ou `Ctrl+C` = Normal Mode.
* `:w` = Salvar as alterações feitas.
* `:q` = Sai do Neovim.
* `:wq` = Salva as alterações e depois fecha o Neovim.

### Movimentação

* `h` `j` `k` `l` = Movimenta um espaço (esquerda, baixo, cima e direita respectivamente. As setas funcionam também).
* `gg` = Vai pro início do arquivo.
* `G` = Vai pro final do arquivo.

### Editar texto

* `dd` = Recorta uma linha.
* `yy` = Copia uma linha.
* `p` = Cola a partir do cursor.
* `u` = Desfaz a última alteração.
* `Ctrl+r` = Refaz.
* `x` = Apaga um caracter.

### Buscar

* `/exemplo` = Busca a palavra "exemplo" no arquivo.
* `n` = Próxima ocorrência da busca.
* `N` = Ocorrência anterior da busca.

## Ambiente Windows

Tenho mais experiência com C#, e o ecossistema Windows. Então falarei mais sobre o **WSL** para usar o **Ubuntu**.

Se você nunca instalou o WSL no seu Windows, esse link te ajudará facilmente: [WSL Install](https://learn.microsoft.com/en-us/windows/wsl/install).
E gostaria de acrescentar que não precisa ficar preso ao Ubuntu, é tranquilo alterar a distribuição.

Depois do WSL instalado, você precisará fazer algumas instalações padrões de ferramentas.

Gosto de usar o `Terminal App`, que já vem instalado por padrão. Caso não esteja disponível, você pode baixá-lo na Microsoft Store.
Mudo o tema, vou nas configurações e seleciono para iniciar o Ubuntu ao abrir o aplicativo e customizo alguns pequenos detalhes estéticos.

## Iniciando no Ubuntu

Do sistema operacional:
```sh
sudo apt update
sudo apt upgrade
```

Ferramentas:
```sh
sudo apt install build-essential curl wget git
sudo apt install unzip tar xz-utils
```

Por padrão, as configurações do Neovim ficam no diretório `~/.config/nvim`, então crie essa pasta se ela ainda não existir:
```sh
mkdir -p ~/.config/nvim
```

## Zsh (Opcional)

Eu customizo o terminal no Ubuntu diferente de como está no Windows, é opcional, você não precisa fazer.
Para isso eu instalo o `zsh` e vou utilizar `ohmyzsh`.
Visualmente me agrada e também ajuda a completar comandos no terminal e etc. Experimente!!
Links para mais informações: [Oh my zsh](https://ohmyz.sh/)

```sh
sudo apt install zsh
```

Depois você precisa definir o zsh como **padrão**.
```sh
chsh -s $(which zsh)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
git clone https://github.com/zsh-users/zsh-autosuggestions.git ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions
```

Agora precisa editar o arquivo e adicionar uma linha. Abra o editor de texto que preferir. Sugiro experimentar o Vim.
```sh
vim ~/.zshrc
```

Acrescente no arquivo ou edite: `plugins=(git zsh-autosuggestions)`

Salve o arquivo, `:w` e feche o editor `:q`.

Voltando pro terminal faça:
```sh
source ~/.zshrc
```

*Importante*: Se encontrar instruções para editar o `.bashrc`, lembre-se de aplicá-las ao `.zshrc`, pois agora está usando Zsh.

## Configuração Manual

Você pode configurar parte por parte seu Neovim. Instalando os plugins que quiser e assim vai.

Começando com criando o arquivo `init.lua` no diretório `~/.config/nvim`.

Eu tenho um repositório com algumas configurações. Dê uma olhada se quiser. Mas eu recomendo seguir com **Kickstart.nvim**.

Se quiser conferir minhas configurações, acesse: [Github - gmessias/init.lua](https://github.com/gmessias/init.lua).

Caso queira clonar o meu repositório e usar o Neovim a partir dele, você precisa instalar `ripgrep` e `fd` para usar o **Telescope** (plugin).

ripgrep
```sh
sudo apt install ripgrep
```

fd
```sh
sudo apt install fd-find
ln -s $(which fdfind) ~/.local/bin/fd
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

Depois só fazer o clone do repositório no diretório `~/.config/nvim`.

## Kickstart.nvim

Essa é a melhor forma para você começar. É bem completo, tem muito mais plugins de ajuda e de qualidade de vida que o meu repositório.

A documentação deles é de fácil leitura e bem explicativa.

[Github - kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim)

O kickstart vem com uma opção muito legal para você treinar e fixar o Neovim.
Depois de fazer os passos do kickstart. Vai pro terminal e digite:
```sh
nvim .
```

Aberto o Neovim, digite: `:Tutor`.

Para aprofundar em mais detalhes, entender direitinho por debaixo dos panos. 
Recomendo fortemente seguir e acompanhar o [TJ DeVries](https://www.youtube.com/@teej_dv).

O Kickstart utiliza o `Mason` para gerenciar alguns plugins de **LSP**, que são **essenciais**.

LSPs (Language Server Protocols) são protocolos que fornecem funcionalidades avançadas para linguagens de programação.
Eles funcionam nos bastidores das IDEs, oferecendo recursos como autocompletar, linting e formatação de código.

Portanto, dependendo da linguagem que você estiver utilizando, será necessário instalar o LSP correspondente.

Exemplos de LSPs para algumas linguagens:
* Rust: `rust-analyzer`.
* C#: `OmniSharp`.
* Go: `gopls`.

Para configurar outros aspectos do Neovim, será necessário editar o arquivo `init.lua`.

## Último recado

**Não desista!!**

Aprender Neovim exige uma curva de aprendizado diferente de simplesmente mudar de uma IDE para outra.
Mas, com paciência e prática, você perceberá um enorme ganho em produtividade e controle sobre seu ambiente de desenvolvimento.

Mantenha firme. Aproveite o processo e curta o trajeto. Futuro será incrível.

Obrigado e até!!

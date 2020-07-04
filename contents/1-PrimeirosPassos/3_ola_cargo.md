# 1.3 Olá Mundo

Cargo é o sistema de construção e gerenciamento de pacotes da Rust. A maior parte da comunidade Rust usa essa ferramenta para gerenciar seus projetos Rust pois o Cargo lida com diversas tarefas para você, como criar seu código, fazer o download das bibliotecas de que seu código depende e criar essas bibliotecas.

Os programas Rust mais simples, como o que escrevemos até agora, não têm dependências. Então, se tivéssemos construído o "Olá, mundo!" projeto com o Cargo, ele usaria apenas a parte do Cargo que lida com a construção do seu código. À medida que você escreve programas Rust mais complexos, adiciona dependências e, se você iniciar um projeto usando o Cargo, será muito mais fácil adicionar dependências.

Como a grande maioria dos projetos da Rust usa Cargo, este tutorial pressupõe que você também esteja usando o Cargo. O Cargo vem instalado com o Rust se você usou os instaladores oficiais. Verifique se o Cargo está instalado inserindo o seguinte em seu terminal:

```sh
cargo --version
```

Se você vir um número de versão, ele está instalado! Se você vir um erro, como `command not found`, consulte a documentação do seu método de instalação para determinar como instalar o Cargo separadamente.

### Criando um projeto com Cargo

Vamos criar um novo projeto usando Cargo e ver como ele difere do nosso projeto original "Olá, mundo!". Volte para o diretório de projetos (ou para onde você decidiu armazenar seu código). Em qualquer sistema operacional, execute o seguinte:

```sh
$ cargo new ola_cargo
$ cd ola_cargo
```

O primeiro comando cria um novo diretório chamado *ola_cargo*. Nomeamos nosso projeto como *ola_cargo* e o Cargo cria seus arquivos em um diretório com o mesmo nome.

Vá para o diretório *ola_cargo* e liste os arquivos. Você verá que o Cargo gerou dois arquivos e um diretório para nós: um arquivo *Cargo.toml* e um diretório *src* com um arquivo *main.rs*.

Também inicializou um novo repositório Git junto com um arquivo *.gitignore*. Os arquivos Git não serão gerados se você executar `cargo new` em um repositório Git existente; você pode substituir esse comportamento usando `cargo new --vcs=git`.

> Nota: Caso não queira utilizar um versionador de codigo use cargo new --vcs=none

Abra *Cargo.toml* no seu editor de texto favorito.

Nome do arquivo: *Cargo.toml*

```toml
[package]
name = "hello_cargo"
version = "0.1.0"
authors = ["Your Name <you@example.com>"]
edition = "2018"

[dependencies]
```

Este arquivo está no formato TOML(Tom's Obvious, Minimal Language), que é o formato de configuração do Cargo.

A primeira linha, [package] é um cabeçalho de seção que indica que as seguintes instruções estão configurando um pacote. À medida que adicionamos mais informações a este arquivo, adicionaremos outras seções.

As próximas quatro linhas definem as informações de configuração que o Cargo precisa para compilar seu programa: o nome, a versão, quem o escreveu e a edição do Rust para usar. O Cargo obtém seu nome e informações de email do seu ambiente; portanto, se essas informações não estiverem corretas, corrija as informações agora e salve o arquivo. Falaremos sobre a editionchave no Apêndice E.

A última linha, [dependencies] é o início de uma seção para você listar qualquer uma das dependências do seu projeto. No Rust, pacotes de código são chamados de *crates*. Não precisaremos de outras crates para este projeto, portanto usaremos essa seção de dependências.

Agora abra *src/main.rs* e dê uma olhada:

Nome do arquivo: src/main.rs

```rust
fn main() {
    println!("Olá, mundo!");
}
```

Cargo gerou um programa `"Olá, mundo!"` para você, exatamente como o que escrevemos anteriormente! Até o momento, as diferenças entre o projeto anterior e o projeto que o Cargo gerou são que Cargo colocou o código no diretório src e temos um arquivo de configuração Cargo.toml no diretório superior.

O Cargo espera que seus arquivos de origem morem dentro do diretório src. O diretório do projeto de nível superior é apenas para arquivos README, informações sobre licença, arquivos de configuração e qualquer outra coisa não relacionada ao seu código. O uso do Cargo ajuda a organizar seus projetos. Há um lugar para tudo, e tudo está no seu lugar.

Se você iniciou um projeto que não usa Cargo, como fizemos com o "Olá, mundo!" projeto, você pode convertê-lo em um projeto que usa Cargo. Mova o código do projeto para o diretório src e crie um arquivo Cargo.toml apropriado.

### Construindo e executando um projeto de carga

Agora vamos ver o que é diferente quando criamos e executamos o "Olá, mundo!" programa com carga! A partir do seu hello_cargo diretório, construir seu projeto, digitando o seguinte comando:

```sh
$ cargo build
   Compiling ola_cargo v0.1.0 (file:///projetos/ola_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.41s
```

Este comando cria um arquivo executável em target/debug/ola_cargo (ou target\debug\ola_cargo.exe no Windows) e não no diretório atual. Você pode executar o executável com este comando:

```cmd
$ ./target/debug/ola_cargo # or .\target\debug\ola_cargo.exe on Windows
Ola, mundo!
```

Se tudo correr bem, `Ola, mundo!` deve imprimir no terminal. A execução `cargo build` pela primeira vez também faz com que o Cargo crie um novo arquivo no nível superior: *Cargo.lock*. Este arquivo mantém o controle das versões exatas das dependências no seu projeto. Este projeto não possui dependências, portanto o arquivo é um pouco esparso. Você nunca precisará alterar esse arquivo manualmente; Cargo gerencia seu conteúdo para você.

Acabamos de criar um projeto cargo build e executá-lo ./target/debug/ola_cargo, mas também podemos usar `cargo run` para compilar o código e, em seguida, executar o executável resultante em um único comando:

```sh
$ cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.02s
     Running `target/debug/ola_cargo`
Ola, mundo!
```

Observe que desta vez não vimos resultados indicando que o Cargo estava compilando `ola_cargo`. Cargo descobriu que os arquivos não haviam mudado, então apenas executou o binário. Se você tivesse modificado seu código-fonte, o Cargo reconstruiria o projeto antes de executá-lo e você teria visto esta saída:

```sh
$ cargo run
   Compiling ola_cargo v0.1.0 (file:///projetos/ola_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.34s
     Running `target/debug/ola_cargo`
Ola, mundo!
```

Cargo também fornece um comando chamado `cargo check`. Este comando verifica rapidamente seu código para garantir que ele seja compilado, mas não produza um executável:

```sh
$ cargo check
   Checking hello_cargo v0.1.0 (file:///projetos/ola_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.32 secs
```

Por que você não gostaria de um executável? Muitas vezes, `cargo check` é muito mais rápido que `cargo build`, porque pula a etapa de produção de um executável. Se você estiver verificando continuamente seu trabalho enquanto escreve o código, o uso do `cargo check` acelerará o processo! Como tal, muitos programadores Rust executam `cargo check` periodicamente enquanto escrevem seu programa para garantir que ele seja compilado. Em seguida, execultam `cargo build` quando estão prontos para usar o executável.

Vamos recapitular o que aprendemos até agora sobre o Cargo:

- Podemos construir um projeto usando cargo buildor cargo check.
- Podemos criar e executar um projeto em uma etapa usando cargo run.
- Em vez de salvar o resultado da compilação no mesmo diretório que o nosso código, o Cargo o armazena no diretório de *destino/depuração*.
Uma vantagem adicional do uso do Cargo é que os comandos são os mesmos, independentemente do sistema operacional em que você está trabalhando. Portanto, neste momento, não forneceremos mais instruções específicas para Linux e macOS versus Windows.

### Build para lançamento

Quando seu projeto estiver finalmente pronto para o lançamento, você poderá usá `cargo build --release` para compilá-lo com otimizações. Este comando criará um executável no *target/release* em vez do *target/debug*. As otimizações tornam seu código Rust mais rápido, mas ativá-los aumenta o tempo necessário para a compilação do seu programa. É por isso que existem dois perfis diferentes: um para desenvolvimento, quando você deseja reconstruir com rapidez e frequência, e outro para criar o programa final que você fornecerá a um usuário que não será reconstruído repetidamente e que será executado o mais rápido possível. Se você estiver comparando o tempo de execução do seu código, certifique-se de executar `cargo build --release` e comparar com o executável em `target/release`.

### Cargo como convenção
Em projetos simples, o Cargo não fornece muito valor apenas com o uso rustc, mas provará seu valor à medida que seus programas se tornam mais complexos. Com projetos complexos compostos por várias caixas, é muito mais fácil deixar o Cargo coordenar a construção.

Embora o projeto `ola_cargo` seja simples, ele agora usa grande parte das ferramentas reais que você usará no restante de sua carreira na Rust. De fato, para trabalhar em qualquer projeto existente, você pode usar os seguintes comandos para verificar o código usando o Git, mudar para o diretório desse projeto e criar:

```sh
$ git clone qualquer-url.com/qualquer-projeto
$ cd qualquer-projeto
$ cargo build
```

Para mais informações sobre carga, consulte a [documentação](https://doc.rust-lang.org/cargo/).

### Resumo

Você já está começando bem na sua jornada Rust! Neste capítulo, você aprendeu como:

- Instalar a versão estável mais recente do Rust usando `rustup`
- Atualizar para uma versão mais recente do Rust
- Abrir documentação instalada localmente
- Escrever e executar um programa `"Olá, mundo!"` usando `rustc` diretamente
- Criar e executar um novo projeto usando Cargo

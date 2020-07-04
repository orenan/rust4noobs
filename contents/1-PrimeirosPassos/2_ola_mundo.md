# 1.2 Olá Mundo

Agora que instalamos o Rust, vamos escrever seu primeiro programa Rust. Quando se aprende uma nova linguagem, é tradicional escrever um pequeno programa que imprime o texto `Olá, mundo!` na tela, então faremos o mesmo aqui!

### Criando o diretório do projeto
Primeiro você deve criar um diretorio para armazenar seu código Rust. Para o Rust não importa onde o seu código mora, mas para os exercícios e projetos, sugerimos criar um diretório de projetos no diretório inicial e manter todos os seus projetos lá.

Em seu terminal digite os seguintes comandos para criar um diretório de projetos e um diretório para o "Olá, mundo!" projeto no diretório de projetos.

Para Linux, macOS e PowerShell no Windows, digite o seguinte:

```sh
$ mkdir ~/projetos
$ cd ~/projetos
$ mkdir ola_mundo
$ cd ola_mundo
```
Para o Windows CMD, digite o seguinte:

```cmd
> mkdir "%USERPROFILE%\projetos"
> cd /d "%USERPROFILE%\projetos"
> mkdir ola_mundo
> cd ola_mundo
```

### Escrevendo e executando um programa Rust
Faça um novo arquivo de origem com o nome `main.rs`. Arquivos Rust sempre terminam com a extensão `.rs`. Se você estiver usando mais de uma palavra no seu nome de arquivo, use um sublinhado para separá-las. Por exemplo, use *hello_world.rs* em vez de *helloworld.rs*.

Agora abra o arquivo `main.rs` que você acabou de criar e insira este código

```rust
fn main() {
    println!("Olá, mundo!");
}
```

Salve o arquivo e vá para seu terminal. No Linux ou macOS, digite os seguintes comandos para compilar e executar o arquivo:

```sh
$ rustc main.rs
$ ./main
Olá, mundo!
```

No Windows, digite o comando .\main.exe em vez de ./main:

```cmd
> rustc main.rs
> .\main.exe
Olá, mundo!
```

Se o seu `Olá, mundo!` imprimiu, parabéns! Você escreveu oficialmente um programa Rust. Isso faz de você um programador da Rust - bem-vindo!

### Anatomia de um programa Rust
Vamos revisar em detalhe o que acontece para seu `Olá, mundo!` seja imprimido na tela. Aqui esta a primeira peça desse quebra cabeça:

```rust
fn main() {

}
```

Estas linhas definem uma função Rust. A função `main` é especial: é sempre a primeira função do código a ser executada em todo programa Rust. A primeira linha declara uma função nomeada `main` que não possui parâmetros e não retorna nada. Se houvesse parâmetros, eles entrariam entre parênteses ().

Além disso, observe que o corpo da função está entre colchetes {}. Rust exige isso em todos os corpos de funções. É bom estilo colocar o colchete de abertura na mesma linha da declaração de função, adicionando um espaço no meio.

Dentro da função `main` está o seguinte código:

```rust
    println!("Olá, mundo!")
```

Esta linha faz todo o trabalho neste pequeno programa: imprime texto na tela. Há quatro detalhes importantes a serem observados aqui. Primeiro, o estilo Rust é usar quatro espaços para identação, não uma tabulação.

Segundo, `println!` chama uma macro Rust. Se chamar uma função, ela será inserida como `println`(sem a `!`). Voltaremos a falar sobre macros mais a frente. Por enquanto, você só precisa saber que usar um `!` meio que você está chamando uma macro em vez de uma função normal.

Terceiro, você vê a string `"Olá, mundo!"`. Passamos essa string como argumento para o `println!` e a string é impressa na tela.

Quarto, terminamos a linha com ponto-e-vírgula (`;`), que indica que essa expressão terminou e a próxima está pronta para começar. A maioria das linhas do código Rust termina com um ponto e vírgula.

### Compilar e executar são etapas separadas
```sh
$ rustc main.rs
```

Se você tem experiência em C ou C ++, notará que isso é semelhante a `gcc` ou `clang`. Após compilar com sucesso, o Rust gera um executável binário.

No Linux, macOS e PowerShell no Windows, você pode ver o executável digitando o comando `ls` no seu terminal. No Linux e macOS, você verá dois arquivos. Com o PowerShell no Windows, você verá os mesmos três arquivos que usaria no CMD.

```sh
$ ls
main  main.rs
```

Com o CMD no Windows, você digitaria o seguinte:

```cmd
> dir /B %= the /B option says to only show the file names =%
main.exe
main.pdb
main.rs
```

Isso mostra o arquivo de código-fonte com a extensão `.rs` , o arquivo executável ( *main.exe* no Windows, mas principal em todas as outras plataformas) e, ao usar o Windows, um arquivo contendo informações de depuração com a extensão .pdb. A partir daqui, você executa o arquivo main ou *main.exe* , assim:

```sh
$ ./main # or .\main.exe on Windows
```

Se main.rs era seu programa "Olá, mundo!", `Olá, mundo!` será impresso no seu terminal.

Diferente de Ruby, Python ou JavaScript, Rust não é uma linguagem dinâmica e sim uma linguagem compilada, o que significa que você pode compilar um programa e fornecer o executável para outra pessoa, e eles podem executá-lo mesmo sem o Rust instalado.

Apenas compilar `rustc` é bom para programas simples, mas à medida que seu projeto cresce, você deseja gerenciar todas as opções e facilitar o compartilhamento de seu código. A seguir, apresentaremos a ferramenta Cargo, que ajudará você a criar programas Rust no mundo real.

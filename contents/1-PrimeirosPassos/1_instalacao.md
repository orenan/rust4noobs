# 1.1 Instalação do Rust

## Instalando
### Linux e macOS e outros Unix-like OS.
Para instalar no Linux ou macOS você deve rodar este comando no terminal:

```sh
$ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```

O comando baixa um script e inicia a instalação da ferramenta rustup, que instala a versão estável mais recente do Rust. Sua senha pode ser solicitada. Se a instalação for bem sucedida, a seguinte linha aparecerá:

```sh
Rust is installed now. Great!
```

Se preferir, faça o download do script e inspecione-o antes de executá-lo.

O script de instalação adiciona Rust automaticamente ao PATH do sistema após o próximo login. Se você deseja começar a usar o Rust imediatamente, em vez de reiniciar o terminal, execute o seguinte comando no shell para adicionar o Rust ao PATH do sistema manualmente:

```sh
$ source $HOME/.cargo/env
```

Como alternativa, você pode adicionar a seguinte linha ao seu ~/.bash_profile:

```sh
$ export PATH="$HOME/.cargo/bin:$PATH"
```

### Windows
A completar...

## Atualizando e desinstalando
Depois de instalar o Rust via rustup, é fácil atualizar para a versão mais recente. No seu terminal, execute o seguinte comando:

```sh
$ rustup update
```

Para desinstalar o Rust e rustup, execute o seguinte comando de desinstalação em seu shell:

```sh
$ rustup self uninstall
```

## Verificando a instalação
Para verificar a instalação execute o seguinte comando:

```sh
$ rustc --version
```

Você deve ver o número da versão, confirmar o hash e confirmar a data da versão estável mais recente lançada no seguinte formato:

```sh
rustc x.y.z (abcabcabc yyyy-mm-dd)
```

## Documentação local
Junto com a instalação do Rust vem uma cópia da documentação localmente, para que você possa a consultar offline. Execute o comando `rustup doc` para abrir a documentação local no seu navegador.

Sempre que um tipo ou função for fornecida pela biblioteca padrão e você não tiver certeza do que faz ou como usá-lo, use a documentação da interface de programação de aplicativos (API) para descobrir!

## Configurando seu editor de texto
Para programar você precisa de um bom editor de texto, em [editores](/contents/Extras/editores.md) você irá ter algumas sugestões e aprenderá a configurar seu editor de texto favorito para programar em Rust

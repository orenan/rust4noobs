# 1.1 Instalação do Rust

## Rustup
### Linux e macOS e outros Unix-like OS.
Para instalar no Linux ou macOS você deve rodar este comando no terminal:
```$ curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh```

O comando baixa um script e inicia a instalação da ferramenta rustup, que instala a versão estável mais recente do Rust. Sua senha pode ser solicitada. Se a instalação for bem sucedida, a seguinte linha aparecerá:
```Rust is installed now. Great!```

Se preferir, faça o download do script e inspecione-o antes de executá-lo.

O script de instalação adiciona Rust automaticamente ao PATH do sistema após o próximo login. Se você deseja começar a usar o Rust imediatamente, em vez de reiniciar o terminal, execute o seguinte comando no shell para adicionar o Rust ao PATH do sistema manualmente:
```$ source $HOME/.cargo/env```

Como alternativa, você pode adicionar a seguinte linha ao seu ~/.bash_profile:
```$ export PATH="$HOME/.cargo/bin:$PATH"```

### Windows
A completar...

## Atualizando e desinstalando
Depois de instalar o Rust via rustup, é fácil atualizar para a versão mais recente. No seu terminal, execute o seguinte comando:
```$ rustup update```

Para desinstalar o Rust e rustup, execute o seguinte comando de desinstalação em seu shell:
```$ rustup self uninstall```

## Verificando a instalação
Para verificar a instalação execute o seguinte comando:
```$ rustc --version```

Você deve ver o número da versão, confirmar o hash e confirmar a data da versão estável mais recente lançada no seguinte formato:
```rustc x.y.z (abcabcabc yyyy-mm-dd)```

## Documentação local
Junto com a instalação do Rust vem uma cópia da documentação localmente, para que você possa a consultar offline. Execute o comando `rustup doc` para abrir a documentação local no seu navegador.

Sempre que um tipo ou função for fornecida pela biblioteca padrão e você não tiver certeza do que faz ou como usá-lo, use a documentação da interface de programação de aplicativos (API) para descobrir!

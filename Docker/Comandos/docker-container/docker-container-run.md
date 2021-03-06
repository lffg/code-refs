# `docker container run (...)`

Roda um comando em específico em um novo container. Irá baixar a imagem se não existir.
Após o `run`, **deve** se passar como argumento o nome da **imagem** a ser baixada, por exemplo:

```shell
docker container run <image-name>
```

## Opções:

#### `--rm`

Remove automaticamente o _container_ após ser finalizado e sair do processo. Isso irá impedir que o _container_ seja exibido na lista de _containers_ (`docker container run ls -a`)_ após ser finalizado.

#### `--tty` (`-t`)

Aloca um pseudo terminal para ser utilizado.

#### `--interactive` (`-i`)

Anexa o _stdin_ do _container_ ao terminal. "Modo interativo".

#### `--name`

Atribui um nome customizado para o _container_ que está sendo criado. Isso é útil para que este mesmo _container_ possa ser reutilizado no futuro.

Exemplo:
```shell
docker container run --name <container-name> <image-name>
```

### `--detach` (`-d`)

Roda o _container_ em modo _background_, emitindo somente o ID do _container_ em atividade.

### `--publish` (`-p`)

Mapeia uma porta interna do _container_ para uma porta externa (que será **exposta** pelo _container_). Essa opção é do tipo **lista**, o que significa que múltiplos mapeamentos de portas podem ser feitos.

Exemplo:
```shell
docker container run -p 8080:80 <image-name>
```

No comando acima, a sintaxe "`8080:80`" define o mapeamento de portas, de modo que:

- O número que **precede** os dois pontos (`8080`) é a porta que será **exposta** pelo _container_;
- O número que **procede** os dois pontos (`80`) é a porta interna do _container_.

### `--volume` (`-v`)

Cria um mapeamento de diretórios, de modo que irá mapear um diretório externo (do computador _host_) para um diretório **interno** ao _container_.

Exemplo:
```shell
docker container run -v /path/to/host/dir:/path/to/internal/container/dir <image-name>
```

No comando acima, a sintaxe "`/path/to/host/dir:/path/to/internal/container/dir`" define o mapeamento de diretórios, de modo que:

- O caminho que **precede** os dois pontos (`/path/to/host/dir`) é o diretório **externo** ao _container_;
- O caminho que **procede** os dois pontos (`/path/to/internal/container/dir`) é o diretório **interno** do _container_.


## Comandos utilizados no curso:

### Executar serviços
```bash
docker-compose up
```
> A flag `-d` não trava o terminal.

### Monitorar logs
```bash
docker-compose logs -f
```

### Comando `docker run` explicado:

- **docker run**: para iniciar um container.
- **--rm**: garante que o container seja removido após a execução.
- **-itv** no comando Docker tem as seguintes funções importantes:
  - **-it**: torna o processo interativo, permitindo que você interaja com o terminal do container. Isso é útil para linkar o nosso terminal com o terminal desse container.
  - **-v**: mapeia um volume, ou seja, cria um vínculo entre a pasta atual do sistema (`$(pwd)`), que captura o caminho do diretório atual, e a pasta `/app` dentro do container.
- **-w /app**: especifica que o diretório de trabalho dentro do container será `/app`.
- **golangci/golangci-lint**: imagem a ser executada.

Em resumo, este comando executa o lint na nossa aplicação usando a ferramenta `golangci`. Para isso, rodamos o comando `golangci-lint run`, seguido pelos nomes das pastas onde o código está localizado: `controllers/`, `database/`, `models/` e `routes/`.

```bash
docker run --rm -itv $(pwd):/app -w /app golangci/golangci-lint golangci-lint run controllers/ database/ models/ routes/
```

Para prosseguir, vamos executar `docker compose up -d` para liberar o terminal para outras tarefas. Em seguida, usaremos o comando `docker compose exec app`, para rodar comandos diretamente no container da aplicação, seguido de `go test main_teste.go`

```bash
docker compose exec app go test main_teste.go
```

### Makefile

```bash
makefile lint
```
```bash
makefile test
```
```bash
makefile start
```
```bash
makefile ci
```


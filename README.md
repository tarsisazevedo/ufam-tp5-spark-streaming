# Projeto de Implementação 5

Este repositorio é base para o [Projeto de Implementação 5](https://docs.google.com/document/d/1htJb8SQSYM0WczqiJqCnuHf7CcgcNvZa/edit?usp=sharing&ouid=110510764865100271570&rtpof=true&sd=true)

### Estrutura do repositorio

A documentação sobre Parquet, pedida no trabalho, deve ser colocada na pasta `docs`

Os dados do arquivo.zip devem ser colocados dentro da pasta `data`, assim como os dados transformados para Parquet.

Seus scripts devem ser criados dentro da pasta `src`. Eles estarão automaticamente disponiveis dentro do container spark.

### Configurando o ambiente local

Para começar, inicialize os containers docker com o comando
```bash
$ docker-compose up
```
Veja se todos os containers estão rodando executando o comando:
```bash
$ docker ps
```

Depois, entre no container kafka e crie os topicos pedidos no trabalho:
```bash
$ docker exec -it kafka_streaming_class-kafka-1 bash
$ kafka-topics --create --replication-factor 1 --bootstrap-server localhost:9092 --topic <nome do topico>
```

Depois dos topicos criados, você pode entrar no container spark e executar seus scripts
```bash
$ docker exec -it kafka_streaming_class-spark-1 bash
$ spark-submit <script x>
$ spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.3.0 <script que fala com kafka>
```
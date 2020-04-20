![Fio de Ariadne](imgs/fio-de-ariadne.jpg)

# Fio de Ariadne

Essa é uma _prova de conceito_ para um sistema de raspagem e estruturação de dados sobre crianças desaparecidas no Brasil. O _Fio de Ariadne_ tem como requisitos técnicos [Python](https://python.org) 3.7+ e [Poetry](https://python-poetry.org/).

## Instalando as dependências

```console
$ poetry install
```

Para utilizar as dependências, você precisa _entrar_ no _virtualenv_ que o Poetry criou:

```console
$ poetry shell
```

Use `exit` para sair do _virtualenv_ quando desejar.

## Configurando a aplicação feita em Django

Execute esse comando e siga as instruções:

```console
$ createnv
```

## Raspando os dados

Esses comandos só precisam ser executados uma única vez. Eles criam a estrutura do banco de dados, raspam os dados e salvam tudo nesse banco:

```console
$ python manage.py migrate
$ python manage.py crawl
```

Você pode ainda criar um usuário para acessar o painel de controle:

```console
$ python manage.py createsuperuser
```

## Iniciando a aplicação web

Utilize esse comando e depois acesse [`localhost:8000`](http://localhost:8000):

```console
$ python manage.py runserver
```

### API web

#### `GET /api/kid`

Lista as crianças do nosso banco de dados.

Aceita como parâmetro de busca (busca exata) parâmetros de URL com os nomes dos campos do modelo `web.core.models.Kid`.

##### Exemplo

`GET /api/kid?eyes=Pretos&hair=Castanho escuro` lista apenas as crianças:

* cujo campo `eyes` tenha o valor exato (_case-sensitive_, inclusive) `"Pretos"`
* **e** cujo campo `hair` tenha o valor exato (_case-sensitive_, inclsuive) `"Castanho escuro"`

## Contribuindo

![Precisamos de ajuda](imgs/fio-de-ariadne-precisa-de-ajuda.jpg)

Você pode contribuir com melhorias no código e utilizar algumas verificações de qualidade:

```console
$ pytest
$ mypy crawler
$ black .
```

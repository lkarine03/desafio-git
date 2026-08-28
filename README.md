# Desafio Git e GitHub

Projeto desenvolvido como parte de um desafio prático envolvendo Git, GitHub, GitHub Actions, Docker e uma API em Python utilizando FastAPI.

## Tecnologias utilizadas

- Python 3.13
- FastAPI
- Pytest
- Docker
- Git e GitHub
- GitHub Actions
- Semgrep
- Docker Hub

## Estrutura do projeto

desafio-git/
├── app/
│   └── main.py
├── tests/
│   └── test_main.py
├── .github/
│   └── workflows/
│       ├── ci.yml
│       └── cd.yml
├── requirements.txt
├── Dockerfile
└── README.md

## API

A API foi desenvolvida utilizando FastAPI.

### Endpoint principal

GET /

Retorno:

{
  "mensagem": "Hello World - CloudOps Pipeline!",
  "status": "online",
  "versao": "1.0.0"
}

### Health Check

GET /health

Retorno:

{
  "status": "healthy"
}

## Como executar o projeto

### Criar e ativar o ambiente virtual

No Windows PowerShell:

    python -m venv .venv

Caso seja necessário permitir a ativação:

    Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass

Ative o ambiente:

    .\.venv\Scripts\Activate.ps1

### Instalar as dependências

    pip install -r requirements.txt

### Executar a API

    uvicorn app.main:app

A API estará disponível na porta 8000.

## Testes

Os testes são executados com Pytest:

    python -m pytest tests/ -v

## Docker

O projeto possui um Dockerfile para criar uma imagem da aplicação.

Para gerar a imagem:

    docker build -t cloudops-api .

Para executar o container:

    docker run -p 8000:8000 cloudops-api

## GitFlow

O projeto utiliza a seguinte organização de branches:

- main: versão principal do projeto.
- develop: branch de desenvolvimento.
- feature/*: branches utilizadas para novas funcionalidades.

Fluxo utilizado:

feature/* → develop → main

As alterações são integradas por meio de Pull Requests.

## Integração Contínua

O workflow de CI é executado em Pull Requests para as branches develop e main.

O pipeline realiza:

- Instalação das dependências.
- Execução dos testes com Pytest.
- Análise de segurança utilizando Semgrep.

## Entrega Contínua

O workflow de CD é executado quando há atualização na branch main.

O pipeline realiza:

- Login no Docker Hub utilizando GitHub Secrets.
- Build da imagem Docker.
- Publicação da imagem no Docker Hub.
- Criação da tag latest.
- Criação de uma tag utilizando o SHA do commit.

## Docker Hub

Imagem publicada em:

lkarine/desafio-git

## GitHub Secrets

Foram configurados:

- DOCKER_USERNAME
- DOCKER_TOKEN

## Autor

Lana Karine da Silva Oliveira


## Contato

lana.oliveira@fellowship.aircompany.ai
# CI/CD com Jenkins e Cypress

Projeto desenvolvido para demonstrar a integração de **testes automatizados com um pipeline de CI/CD utilizando Jenkins**.

A proposta é automatizar a execução dos testes Cypress por meio de um pipeline, permitindo que a aplicação tenha sua suíte de testes executada de forma padronizada durante o processo de integração contínua.

## 🎯 Objetivo

Demonstrar na prática como uma ferramenta de CI/CD pode ser utilizada para incorporar testes automatizados ao processo de desenvolvimento.

O pipeline é responsável por:

1. Instalar as dependências do projeto;
2. Executar os testes automatizados;
3. Identificar se a execução foi concluída com sucesso ou apresentou falhas;
4. Informar o resultado da execução no Jenkins.

Dessa forma, a qualidade deixa de depender exclusivamente da execução manual dos testes e passa a fazer parte do fluxo automatizado de integração.

## 🛠️ Tecnologias utilizadas

* **Jenkins** — automação do pipeline CI/CD
* **Cypress** — automação de testes end-to-end
* **JavaScript** — linguagem utilizada nos testes
* **Node.js / npm** — gerenciamento das dependências e execução dos scripts
* **Git** — versionamento do projeto

## 📂 Estrutura do projeto

```text
├── cypress/
│   └── e2e/
│       └── ...
│
├── .gitignore
├── Jenkinsfile
├── cypress.config.js
├── package.json
└── package-lock.json
```

## 🔄 Pipeline

O pipeline está definido no arquivo `Jenkinsfile` e utiliza um agente Jenkins com Node.js configurado.

O fluxo principal é:

```text
        ┌───────────────┐
        │   Jenkins     │
        └───────┬───────┘
                │
                ▼
     ┌─────────────────────┐
     │ Instala dependências │
     │     npm install      │
     └──────────┬──────────┘
                │
                ▼
     ┌─────────────────────┐
     │ Executa os testes   │
     │       npm test      │
     └──────────┬──────────┘
                │
          ┌─────┴─────┐
          ▼           ▼
       Sucesso       Falha
          │           │
          ▼           ▼
       Pipeline     Pipeline
       aprovado     reprovado
```

### Etapas do pipeline

#### 1. Instalação das dependências

O Jenkins executa:

```bash
npm install
```

Essa etapa prepara o ambiente necessário para a execução dos testes.

#### 2. Execução dos testes

Após a instalação das dependências, o pipeline executa:

```bash
npm test
```

A execução utiliza os scripts definidos no `package.json` para iniciar os testes automatizados.

#### 3. Resultado da execução

O pipeline possui tratamentos distintos para os cenários de sucesso e falha.

Em caso de sucesso, o Jenkins informa que o build e os testes foram concluídos.

Em caso de falha, o pipeline informa que houve uma falha durante sua execução.

## 🧪 Estratégia de qualidade

A principal finalidade deste projeto é demonstrar a integração entre **automação de testes e integração contínua**.

A ideia é que os testes automatizados sejam executados de maneira consistente sempre que o pipeline for acionado.

Esse modelo permite identificar problemas mais cedo no ciclo de desenvolvimento e reduz a dependência da execução manual para validações repetitivas.

## ▶️ Execução local

Para executar os testes localmente, é necessário ter o **Node.js** instalado.

Clone o repositório:

```bash
git clone https://github.com/Patrick-Venturini/ci-cd-exemplo-jenkins.git
```

Acesse o diretório:

```bash
cd ci-cd-exemplo-jenkins
```

Instale as dependências:

```bash
npm install
```

Execute os testes:

```bash
npm test
```

## ⚙️ Execução utilizando Jenkins

Para executar o projeto através do Jenkins:

1. Configure uma instância do Jenkins;
2. Instale e configure o Node.js no Jenkins;
3. Crie um novo Pipeline;
4. Vincule o pipeline ao repositório Git;
5. Configure o Jenkins para utilizar o `Jenkinsfile` presente no projeto;
6. Execute o pipeline.

O Jenkins será responsável por executar as etapas definidas no arquivo:

```text
Jenkinsfile
```

## 📚 Aprendizados

Este projeto permitiu praticar conceitos relacionados a:

* Integração contínua;
* Pipelines;
* Jenkinsfile;
* Automação da execução de testes;
* Integração entre Jenkins e Node.js;
* Execução de testes Cypress em pipeline;
* Identificação automática de falhas;
* Qualidade integrada ao processo de entrega.

## 🚀 Próximos passos

Como evolução do projeto, algumas melhorias possíveis seriam:

* Executar o pipeline automaticamente a cada alteração no repositório;
* Configurar Webhooks para disparar builds;
* Publicar relatórios dos testes no Jenkins;
* Armazenar screenshots e vídeos de testes que falharem;
* Adicionar diferentes ambientes de execução;
* Integrar análise de qualidade ao pipeline;
* Adicionar etapas de validação antes da execução dos testes.

## 👨‍💻 Sobre o projeto

Este projeto faz parte do meu portfólio de **Qualidade de Software**, com foco no desenvolvimento de conhecimentos práticos em automação de testes, CI/CD e Engenharia de Qualidade.

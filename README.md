![Logo](logo.png)

# Desafio Automação BugBank

A aplicação web [BugBank](https://bugbank.netlify.app) simula um módulo financeiro, possibilitando registros de contas de usuário que também funcionam como contas bancárias capazes de efetuar transferências de valores monetários para outras contas também registradas.

## Getting started

### Pré-requisitos

- [Git](https://git-scm.com/downloads)

> [!NOTE]
> Em ambientes Windows, confirmar também o correto funcionamento do Git Bash

### Obtendo o boilerplate Java

O [boilerplate Java para automação de testes de aplicações web](https://github.com/dbserver/boilerplate-automacao-web-java) contém um conjunto inicial de recursos que possibilitam um rápido e simplificado início de construção de testes automatizados utilizando a proposta "DB" do modelo [PageObject](https://martinfowler.com/bliki/PageObject.html).

Ele é obtido via o script `get_boilerplate.sh`, que também atualiza este arquivo README com as informações sobre configurações necessárias e instruções de execução.

#### 1. Via terminal de comandos (Linux e MacOS)

Tornar o script `get_boilerplate.sh` executável
```shell
chmod +x get_boilerplate.sh
```

Executar o script `get_boilerplate.sh`
```shell
./get_boilerplate.sh
```

#### 2. Via Git Bash (Windows)

Executar o script `get_boilerplate.sh`
```shell
./get_boilerplate.sh
```

## Desafio

### 1. Automation Request

#### Caso de Teste (TC - Test Case):

Registro de uma nova conta de usuário

#### Descrição:

Validar o registro de uma nova conta de usuário através de uma tentativa de acesso bem sucedida.

#### Pré-Condições:

- A aplicação web deve estar acessível
- O usuário ainda não deve ter uma conta registrada

#### Passos:

1. Abrir a página inicial da aplicação web
2. Clicar no botão `Registrar`
3. Preencher o formulário de registro com informações válidas do usuário (E-mail, Nome, Senha e Confirmação senha).
4. Ativar a opção `Criar conta com saldo?`
5. Clicar no botão `Cadastrar`
6. Clicar no botão `Fechar` da mensagem de "criada com sucesso"
7. Preencher o formulário de acesso com informações válidas da conta do usuário (E-mail e Senha)
8. Clicar no botão `Acessar`

#### Resultados Esperados:

- Após o registro, uma mensagem de "criada com sucesso" deve ser exibida
- Após o acesso, uma tela de gestão da conta deve ser exibida contendo um elemento de "Saldo em conta"

#### Pós-Condições:

- O usuário deve estar com a nova conta registrada e ter a acessado com sucesso

### 2. Automation Request

#### Caso de Teste (TC - Test Case):

Transferência de valores monetários entre contas de usuário

#### Descrição:

Validar em uma conta de usuário destinatária a entrada de um valor monetário proveniente de uma conta de usuário originária.

#### Pré-Condições:

- A aplicação web deve estar acessível
- Devem haver duas contas de usuário já registradas (originária e destinatária), tendo a conta originária um "Saldo em conta" de R$ 1000,00, e a conta destinatária um "Saldo em conta" de R$ 0,00

#### Passos:

1. Abrir a página inicial da aplicação web
2. Preencher o formulário de acesso com informações válidas da conta de usuário originária (E-mail e Senha)
3. Clicar no botão `Acessar`
4. Clicar no botão `Transferência`
5. Preencher o formulário de transferência com informações válidas para execução da transferência (Número da conta de usuário destinatária, Dígito da conta de usuário destinatária, Valor e Descrição) - O valor deve ser de R$ 500,00
6. Clicar no botão `Transferir agora`
7. Clicar no botão `Fechar` da mensagem de "realizada com sucesso"
8. Clicar no botão `Sair`
9. Preencher o formulário de acesso com informações válidas da conta de usuário destinatária (E-mail e Senha)
10. Clicar no botão `Acessar`

#### Resultados Esperados:

- Após a transferência, a conta de usuário originária deve estar com seu "Saldo em conta" em R$ 500,00
- Após o acesso à conta de usuário destinatária, a mesma deve estar com seu "Saldo em conta" em R$ 500,00

#### Pós-Condições:

- As duas contas de usuário devem estar com valores iguais no seu "Saldo em conta"

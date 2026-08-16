![poster](./.github/poster.png)

# Testes Contínuos com Robot Framework & GitHub Actions

Seja bem-vindo(a) ao meu projeto! Desenvolvi este repositório para demonstrar a implementação de testes de ponta a ponta (E2E) em uma aplicação web de autenticação, utilizando o **Robot Framework** integrado à **Browser Library** (Playwright) e automatizado via pipelines de CI/CD com o **GitHub Actions**.

O objetivo principal deste projeto é garantir a qualidade e a regressão rápida da camada de login do sistema [LoginXP](https://loginxp.vercel.app), aplicando boas práticas de arquitetura de testes (divisão em camadas de ações e recursos) e reporte automatizado.

---

## 🛠️ Tecnologias Utilizadas

- **[Robot Framework](https://robotframework.org/)**: Framework principal para automação de testes baseada em palavras-chave.
- **[Browser Library](https://marketsquare.github.io/robotframework-browser/):** Biblioteca moderna de testes baseada em **Playwright** para automação de navegadores de alta performance.
- **[Python 3.12](https://www.python.org/)**: Linguagem de suporte para execução da suíte de testes.
- **[Node.js 22](https://nodejs.org/)**: Necessário para a inicialização e execução dos drivers do Browser Library.
- **[GitHub Actions](https://github.com/features/actions)**: Esteira de CI/CD para execução contínua dos testes em cada push ou pull request.
- **Docker**: Utilizado na esteira para geração e publicação do relatório de testes (`joonvena/robot-reporter`).

---

## 🚀 Funcionalidades Cobertas

A suíte de testes abrange cenários críticos do fluxo de autenticação:

- **Login com Sucesso (`@smoke`)**: Valida o acesso à aplicação com credenciais válidas e verifica a exibição da mensagem de boas-vindas.
- **Validação de Senha Incorreta**: Garante a exibição do alerta adequado ao informar credenciais inválidas.
- **Validação de Usuário Não Cadastrado**: Garante que usuários inexistentes não tenham acesso ao sistema.
- **Obrigatoriedade do Campo Usuário**: Valida o alerta exibido ao tentar logar sem preencher o nome de usuário.
- **Obrigatoriedade do Campo Senha**: Valida o alerta exibido ao tentar logar sem preencher a senha.
- **Evidências Automatizadas**: Captura automática de telas (*screenshots*) do modal/toast e ao término da execução.

---

## 📋 Pré-requisitos

Antes de começar, certifique-se de ter as seguintes ferramentas instaladas em sua máquina:

- [Python 3.12](https://www.python.org/downloads/) ou superior
- [Node.js 22](https://nodejs.org/en) ou superior
- [Git](https://git-scm.com/)

---

## 🔧 Instalação

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   cd seu-repositorio
   ```

2. **Instale as dependências do Python:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Inicialize a biblioteca do Browser (Playwright):**
   ```bash
   rfbrowser init
   ```

---

## 🧪 Como Executar os Testes

Abaixo estão os comandos para executar os testes localmente em diferentes modos:

### 1. Execução em Modo Headless (Sem interface gráfica - Padrão de CI)
```bash
robot -d ./logs -v IS_HEADLESS:True tests
```

### 2. Execução em Modo Assistido (Exibindo o navegador)
```bash
robot -d ./logs -v IS_HEADLESS:False tests
```

### 3. Execução Apenas dos Testes de Fumaça (Smoke Tests)
```bash
robot -d ./logs -i smoke tests
```

> 💡 **Nota:** Todos os relatórios e evidências (*screenshots*) serão salvos na pasta `./logs`.

---

## ⚙️ Integração Contínua (CI/CD)

Configurei uma pipeline no **GitHub Actions** (`.github/workflows/tests.yml`) que é disparada automaticamente a cada `push` ou `pull_request` direcionado para a branch `main`.

A esteira realiza os seguintes passos:
1. Prepara o ambiente com Node.js 22 e Python 3.12.
2. Instala as dependências e inicializa o `rfbrowser`.
3. Executa os testes marcados com a tag `smoke`.
4. Gera um resumo do relatório diretamente no Pull Request através do container Docker `robot-reporter`.
5. Salva os artefatos de logs (`robot-logs`) por padrão no repositório.

---

## 🤝 Como Contribuir

Contribuições são sempre bem-vindas! Se você quiser melhorar os testes, adicionar novos cenários ou aprimorar a documentação, siga os passos:

1. Faça um **Fork** deste repositório.
2. Crie uma branch para a sua funcionalidade: `git checkout -b feature/minha-nova-feature`.
3. Faça o commit das suas alterações: `git commit -m 'feat: Adiciona novo cenário de teste'`.
4. Envie as alterações para a sua branch: `git push origin feature/minha-nova-feature`.
5. Abra um **Pull Request**.

---

## 📜 Licença

Este projeto está sob a licença [MIT](LICENSE). Sinta-se à vontade para utilizá-lo, modificá-lo e compartilhá-lo.

---

## ✉️ Contato

Projeto desenvolvido por **Seu Nome**.

- **LinkedIn:** [linkedin.com/in/seu-perfil](https://linkedin.com/in/seu-perfil)
- **GitHub:** [@seu-usuario](https://github.com/seu-usuario)
- **E-mail:** seu-email@exemplo.com
- **Curso de Origem:** [QAxperience](https://qax.com.br)
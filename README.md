# Cofre Comunitário 🏦 (Community Vault)

> Projeto submetido ao **[Scaffold-Stellar Hackathon](https://dorahacks.io/hackathon/scaffoldstellar/detail)** (Novembro 2025).

Este é um dApp (Aplicativo Descentralizado) que implementa um "Cofre Comunitário" na rede Stellar. Ele permite que múltiplos usuários depositem fundos (XLM) de forma segura em um único smart contract (Soroban), criando um fundo coletivo transparente e acessível a todos.

-----

## Demo Ao Vivo

**Acesse o dApp "deployado":** [LINK\_DO\_DEPLOY\_AQUI] *(Substitua pelo seu link do Vercel/Netlify)*

-----

## 🚀 Tecnologias Utilizadas

Este projeto foi construído 100% com o stack exigido pelo hackathon, utilizando o `scaffold-stellar` como base:

  * **Frontend:** React, TypeScript, Vite
  * **Backend (Smart Contract):** Rust (Soroban)
  * **Conexão (Wallet):** Stellar Wallet Kit
  * **Rede:** Stellar Testnet

## ✨ Funcionalidades do MVP

O Produto Mínimo Viável (MVP) foca nas interações essenciais do cofre:

  * **Conectar Carteira:** Integração completa com o Stellar Wallet Kit (Freighter, etc.).
  * **Visualizar Saldo Total:** Exibe o saldo total de XLM mantido dentro do smart contract, atualizado em tempo real.
  * **Depositar Fundos:** Permite que qualquer usuário conectado envie fundos (XLM) para o contrato do cofre.
  * **Ver Administrador:** Exibe publicamente o endereço da carteira que fez o "deploy" (instanciação) do contrato.

-----

## ⚙️ Rodando o Projeto Localmente

Siga estas etapas para configurar e rodar o projeto em sua máquina local para desenvolvimento ou teste.

### Pré-requisitos

Antes de começar, certifique-se de ter o seguinte instalado:

  * [Node.js](https://nodejs.org/) (v18+)
  * [Rust](https://www.rust-lang.org/tools/install)
  * [Soroban CLI](https://www.google.com/search?q=https://stellar.org/soroban/docs/getting-started/setup)
  * Uma carteira Stellar (como [Freighter](https://freighter.app/)) configurada para a **Testnet** e com fundos (XLM) da Testnet.

-----

### 1\. Clonar o Repositório

```bash
git clone [URL_DO_SEU_REPOSITORIO_AQUI]
cd [NOME_DA_PASTA_DO_PROJETO]
```

### 2\. Instalar Dependências (Frontend)

Na raiz do projeto, instale os pacotes NPM:

```bash
npm install
```

### 3\. Compilar e Deployar o Contrato (Backend)

O `scaffold-stellar` facilita este processo.

```bash
# Navegue até a pasta do contrato
cd contract

# Construa (compile) o contrato Rust para Wasm
soroban contract build

# Faça o deploy na Testnet (isso exigirá sua carteira/identidade)
# Guarde o "Contract ID" retornado!
soroban contract deploy \
  --wasm target/wasm32-unknown-unknown/release/soroban_community_vault_contract.wasm \
  --source [SUA_IDENTIDADE_SECRET_KEY_OU_NOME] \
  --network testnet
```

### 4\. Configurar o Frontend

Após o deploy (passo 3), você receberá um **Contract ID** (ex: `CC...`).

1.  Volte para a pasta raiz (`cd ..`).

2.  Renomeie o arquivo `.env.example` para `.env`.

3.  Abra o arquivo `.env` e cole o seu Contract ID:

    ```.env
    VITE_CONTRACT_ID=[SEU_CONTRACT_ID_COLADO_AQUI]
    ```

### 5\. Rodar o App (Frontend)

Com o contrato "deployado" e o `.env` configurado, inicie o servidor de desenvolvimento:

```bash
npm run dev
```

Acesse `http://localhost:5173` (ou a porta indicada) no seu navegador.

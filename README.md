# Delivery API com Autenticação JWT e Controle de Acesso (FastAPI)

API RESTful desenvolvida com FastAPI para gerenciamento de usuários e pedidos, contando com autenticação robusta via JWT, controle de acesso baseado em níveis de permissão (RBAC) e regras de negócio automatizadas.

---

## ✨ Features

- 🔐 **Autenticação JWT**: Estratégia completa utilizando Access Token e Refresh Token.
- 👥 **Controle de Acesso Baseado em Níveis (RBAC)**:
  - **Usuário Comum**: Gerencia, altera e cancela exclusivamente os seus próprios pedidos.
  - **Administrador**: Possui acesso global para visualizar e listar todas as ordens cadastradas no sistema.
- 📦 **Gestão de Pedidos**: Fluxo completo de inclusão e remoção de itens em ordens de serviço.
- 💰 **Cálculo Automático de Preços**: Regra de negócio integrada via ORM para recalcular o valor total do pedido automaticamente sempre que houver alteração em seus itens.
- 🗄️ **Versionamento de Banco de dados**: Migrações e evolução de tabelas gerenciadas de forma ágil com Alembic.
- ✅ **Validação Estrita de Dados**: Uso intensivo de modelos Pydantic para garantir a integridade dos dados de entrada.
- 🔄 **Suporte a Login Integrado**: Compatibilidade com o ecossistema de formulários nativos da interface Swagger UI.

---

## 🛠️ Tecnologias Utilizadas

- **FastAPI** → Framework web moderno de alta performance e rápida documentação.
- **SQLAlchemy** → ORM utilizado para abstração, mapeamento e manipulação de entidades relacionais.
- **SQLite** → Banco de dados relacional leve adotado para agilidade no ambiente de desenvolvimento.
- **Alembic** → Controle de versão de banco de dados e gerenciamento de esquemas de migração.
- **JWT (JSON Web Token)** → Mecanismo de segurança padronizado para troca segura de dados entre cliente e servidor.
- **Bcrypt** → Algoritmo de hash criptográfico seguro empregado para a proteção e armazenamento de senhas.
- **Pydantic** → Biblioteca para validação de dados em runtime e definição de contratos de dados (Schemas).

---

## 🔒 Segurança e Autenticação

O sistema emprega práticas modernas de segurança backend:
- Geração de tokens de acesso de curta duração (Access Token).
- Geração de tokens de renovação de longa duração (Refresh Token).
- Armazenamento exclusivo de senhas sob formato de Hash gerado pelo Bcrypt.
- Injeção de dependências nativa do FastAPI para proteção e validação estrita de rotas privadas.

---

## ⚙️ Como Executar o Projeto Localmente

### 1. Clonar o repositório
Execute o comando abaixo no seu terminal (remova o espaço inicial se houver):
```bash
git clone https://github.com/SLNhe/fastapi-delivery-api.git 
cd fastapi-delivery-api
```

### 2. Criar e Ativar o Ambiente Virtual
```bash
python -m venv .venv

# Comando para Ativação no Windows:
.venv\Scripts\activate

# Comando para Ativação no Linux/Mac:
source .venv/bin/activate
```

### 3. Instalar as Dependências do Sistema
```bash
pip install -r requirements.txt
```

### 4. Configurar as Variáveis de Ambiente
Crie um arquivo chamado `.env` na raiz do seu projeto com base na estrutura do `.env.example` e forneça a sua chave secreta privada:
```ini
SECRET_KEY=sua_chave_secreta_privada_aqui
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

### 5. Executar as Migrações do Banco de Dados
```bash
alembic upgrade head
```

### 6. Inicializar o Servidor local
```bash
uvicorn main:app --reload
```

Após iniciar o servidor, abra o seu navegador e acesse a documentação interativa oficial gerada automaticamente pelo Swagger em: **http://127.0.0.1:8000/docs**

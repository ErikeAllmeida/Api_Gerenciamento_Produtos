# Documentação da API de Gerenciamento de Produtos

## Descrição Geral

Esta API permite a criação, leitura, atualização e exclusão de produtos (CRUD) em um sistema simples. Os dados são armazenados em um array na memória, e todas as requisições que criam ou atualizam produtos passam por validação para garantir que os dados estejam corretos.

Foi desenvolvida com o objetivo de fornecer uma interface leve e funcional para manipulação de produtos, servindo como base para aplicações mais complexas.

---

## Objetivos

- Facilitar a manipulação de produtos via API RESTful.
- Garantir que os dados enviados estejam válidos antes de serem processados.
- Prover uma estrutura simples e organizada para futuras expansões.

---

## Funcionalidades

- **Criar Produto:** Adiciona um novo produto com nome e preço.
- **Listar Produtos:** Recupera todos os produtos cadastrados.
- **Buscar Produto:** Busca um produto pelo seu ID.
- **Atualizar Produto:** Atualiza os dados de um produto existente.
- **Excluir Produto:** Remove um produto pelo seu ID.
- **Validação:** Utiliza o Joi para garantir a integridade dos dados enviados.

---

## Tecnologias Utilizadas

| Tecnologia       | Versão       | Descrição                                   |
|------------------|--------------|---------------------------------------------|
| **Node.js**      | 18.x (exemplo) | Ambiente de execução JavaScript server-side |
| **Express.js**   | ^5.1.0       | Framework para criação de APIs REST          |
| **Joi**          | ^17.13.3     | Biblioteca para validação de dados           |
| **NPM**          | Última       | Gerenciador de pacotes                        |

---

## Endpoints

### 1. Listar Produtos

- **URL:** `/api/products`
- **Método:** `GET`
- **Descrição:** Retorna todos os produtos cadastrados.
- **Resposta de sucesso:**

```json
[
  {
    "id": 1,
    "name": "Produto A",
    "price": 100.00
  },
  {
    "id": 2,
    "name": "Produto B",
    "price": 50.50
  }
]
 
  Buscar Produto por ID
URL: /api/products/:id

Método: GET

Parâmetros:

id (inteiro): ID do produto a ser buscado.

Resposta de sucesso:

json
Copiar
Editar
{
  "id": 1,
  "name": "Produto A",
  "price": 100.00
}
Resposta de erro (produto não encontrado):

json
Copiar
Editar
{
  "message": "Produto não encontrado"
}
3. Criar Produto
URL: /api/products

Método: POST

Cabeçalhos:

pgsql
Copiar
Editar
Content-Type: application/json
Corpo (JSON):

json
Copiar
Editar
{
  "name": "Novo Produto",
  "price": 75.00
}
Validação:

name: obrigatório, string, mínimo 3 caracteres

price: obrigatório, número positivo

Resposta de sucesso:

json
Copiar
Editar
{
  "id": 3,
  "name": "Novo Produto",
  "price": 75.00
}
Resposta de erro (validação falhou):

json
Copiar
Editar
{
  "message": "\"name\" length must be at least 3 characters long"
}
4. Atualizar Produto
URL: /api/products/:id

Método: PUT

Parâmetros:

id (inteiro): ID do produto a ser atualizado.

Cabeçalhos:

pgsql
Copiar
Editar
Content-Type: application/json
Corpo (JSON):

json
Copiar
Editar
{
  "name": "Produto Atualizado",
  "price": 120.00
}
Resposta de sucesso:

json
Copiar
Editar
{
  "id": 3,
  "name": "Produto Atualizado",
  "price": 120.00
}
Resposta de erro (produto não encontrado):

json
Copiar
Editar
{
  "message": "Produto não encontrado"
}
5. Excluir Produto
URL: /api/products/:id

Método: DELETE

Parâmetros:

id (inteiro): ID do produto a ser excluído.

Resposta de sucesso: Status 204 No Content (sem conteúdo)

Resposta de erro (produto não encontrado):

json
Copiar
Editar
{
  "message": "Produto não encontrado"
}

Como Executar a API
Clone o repositório:

bash
Copiar
Editar
git clone https://github.com/seu-usuario/nome-do-repositorio.git
Acesse o diretório do projeto:

bash
Copiar
Editar
cd nome-do-repositorio
Instale as dependências:

bash
Copiar
Editar
npm install
Inicie o servidor:

bash
Copiar
Editar
node index.js
A API estará disponível em:

bash
Copiar
Editar
http://localhost:3000/api/products
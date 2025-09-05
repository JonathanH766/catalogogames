# Game Catalogo API

Uma API RESTful para catalogar jogos, construída com Java 21, Spring Boot 3.3.3 e Maven.

## Funcionalidades

- CRUD  para gerenciar jogos.
- Busca de jogos por gênero.
- Validação de dados na criação e atualização.
- Banco de dados em memória H2.

## Pré-requisitos

- Java 17
- Apache Maven

## Como Executar

1. Clone este repositório.  
2. Navegue até o diretório raiz do projeto (`game-catalogo`).
3. Execute o seguinte comando no seu terminal:

   ```bash
   mvn spring-boot:run
   ```

4. A API estará disponível em `http://localhost:8080`.
5. Você pode acessar o console do banco de dados H2 em `http://localhost:8080/h2-console` (use o JDBC URL `jdbc:h2:mem:gamedb`, usuário `sa` e deixe a senha em branco).

---

## Endpoints da API

O caminho base para todos os endpoints é `/api/games`.

### 1. Criar um Jogo

- **Método:** `POST`
- **Endpoint:** `/api/games`
- **Corpo da Requisição (JSON):**
  ```json
  {
    "title": "The Witcher 3: Wild Hunt",
    "genre": "Action RPG",
    "platform": "PC",
    "releaseYear": 2015
  }
  ```
- **Resposta de Sucesso (201 Created):**
  ```json
  {
    "id": 1,
    "title": "The Witcher 3: Wild Hunt",
    "genre": "Action RPG",
    "platform": "PC",
    "releaseYear": 2015
  }
  ```

### 2. Listar todos os Jogos

- **Método:** `GET`
- **Endpoint:** `/api/games`
- **Resposta de Sucesso (200 OK):**
  ```json
  [
    {
      "id": 1,
      "title": "The Witcher 3: Wild Hunt",
      "genre": "Action RPG",
      "platform": "PC",
      "releaseYear": 2015
    }
  ]
  ```

### 3. Buscar Jogos por Gênero

- **Método:** `GET`
- **Endpoint:** `/api/games?genre=rpg`
- **Resposta de Sucesso (200 OK):**
  ```json
  [
    {
      "id": 1,
      "title": "The Witcher 3: Wild Hunt",
      "genre": "Action RPG",
      "platform": "PC",
      "releaseYear": 2015
    }
  ]
  ```

### 4. Buscar Jogo por ID

- **Método:** `GET`
- **Endpoint:** `/api/games/1`
- **Resposta de Sucesso (200 OK):**
  ```json
  {
    "id": 1,
    "title": "The Witcher 3: Wild Hunt",
    "genre": "Action RPG",
    "platform": "PC",
    "releaseYear": 2015
  }
  ```
- **Resposta de Erro (404 Not Found):**
  ```json
  {
    "message": "Game not found with id: 99"
  }
  ```

### 5. Atualizar um Jogo

- **Método:** `PUT`
- **Endpoint:** `/api/games/1`
- **Corpo da Requisição (JSON):**
  ```json
  {
    "title": "The Witcher 3: Wild Hunt - Complete Edition",
    "genre": "Action RPG",
    "platform": "PC/PS5/Xbox Series X",
    "releaseYear": 2016
  }
  ```
- **Resposta de Sucesso (200 OK):**
  ```json
  {
    "id": 1,
    "title": "The Witcher 3: Wild Hunt - Complete Edition",
    "genre": "Action RPG",
    "platform": "PC/PS5/Xbox Series X",
    "releaseYear": 2016
  }
  ```

### 6. Deletar um Jogo

- **Método:** `DELETE`
- **Endpoint:** `/api/games/1`
- **Resposta de Sucesso:** `204 No Content` (sem corpo de resposta).

# Joke API

This is a simple REST API for managing jokes. The API is built using Express.js and provides endpoints to retrieve, create, update, and delete jokes. It also includes rate limiting and a master key-based access control for modifying jokes.

## Table of Contents

- [Installation](#installation)
- [Configuration](#configuration)
- [Endpoints](#endpoints)
- [Error Handling](#error-handling)
- [License](#license)

## Installation

To get started, clone this repository and install the necessary dependencies.

1. **Clone the repository:**
    ```bash
    git clone https://github.com/nikitaahire302/My1st_API.git
    cd joke-api
    ```

2. **Install dependencies:**
    ```bash
    npm install
    ```

   Alternatively, if you're using yarn:
    ```bash
    yarn install
    ```

## Configuration

1. **Environment Variables:**

   Create a `.env` file in the root directory of your project and add the following environment variables:
    ```plaintext
    PORT=3000
    ```

2. **Master Key:**

   The master key used for authorization when creating, updating, or deleting jokes is hardcoded in the code (`4VGP2DN-6EWM4SJ-N6FGRHV-Z3PR3TT`). Change this key in the code if needed.

## Endpoints

### 1. GET a Random Joke
**Endpoint:** `/jokes/random`  
**Method:** `GET`  
**Description:** Retrieves a random joke from the collection.  
**Response:** A random joke object.

### 2. GET a Specific Joke
**Endpoint:** `/jokes/:id`  
**Method:** `GET`  
**Description:** Retrieves a joke by its ID.  
**Parameters:**
- `id` (integer): The ID of the joke to retrieve.  
**Response:** The joke object if found, otherwise a 404 error.

### 3. GET Jokes by Type
**Endpoint:** `/jokes`  
**Method:** `GET`  
**Description:** Retrieves jokes filtered by type. If no type is provided, all jokes are returned.  
**Query Parameters:**
- `type` (string, optional): The type of joke to filter by.  
**Response:** An array of joke objects.

### 4. POST a New Joke
**Endpoint:** `/jokes`  
**Method:** `POST`  
**Description:** Creates a new joke. Requires a master key for authorization.  
**Headers:**
- `x-master-key` (string): The master key for authorization.  
**Request Body:**
- `jokeText` (string): The text of the joke.
- `jokeType` (string): The type of the joke.  
**Response:** The newly created joke object.

### 5. PUT a Joke
**Endpoint:** `/jokes/:id`  
**Method:** `PUT`  
**Description:** Updates an existing joke. Requires a master key for authorization.  
**Headers:**
- `x-master-key` (string): The master key for authorization.  
**Parameters:**
- `id` (integer): The ID of the joke to update.  
**Request Body:**
- `jokeText` (string, optional): The new text of the joke.
- `jokeType` (string, optional): The new type of the joke.  
**Response:** The updated joke object if found, otherwise a 404 error.

### 6. PATCH a Joke
**Endpoint:** `/jokes/:id`  
**Method:** `PATCH`  
**Description:** Partially updates an existing joke. Requires a master key for authorization.  
**Headers:**
- `x-master-key` (string): The master key for authorization.  
**Parameters:**
- `id` (integer): The ID of the joke to update.  
**Request Body:**
- `jokeText` (string, optional): The new text of the joke.
- `jokeType` (string, optional): The new type of the joke.  
**Response:** The updated joke object if found, otherwise a 404 error.

### 7. DELETE a Specific Joke
**Endpoint:** `/jokes/:id`  
**Method:** `DELETE`  
**Description:** Deletes a specific joke by ID. Requires a master key for authorization.  
**Headers:**
- `x-master-key` (string): The master key for authorization.  
**Parameters:**
- `id` (integer): The ID of the joke to delete.  
**Response:** Status code 204 (No Content) if successful, otherwise a 404 error.

### 8. DELETE All Jokes
**Endpoint:** `/jokes`  
**Method:** `DELETE`  
**Description:** Deletes all jokes from the collection. Requires a master key for authorization.  
**Headers:**
- `x-master-key` (string): The master key for authorization.  
**Response:** Status code 204 (No Content) if successful.

## Error Handling

The API includes centralized error handling. If an error occurs during a request, the server will respond with a 500 status code and the message "Something broke!".

# My1st_API

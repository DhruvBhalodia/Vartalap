# Vartalap

## Table of Contents

*   [About VartaLap](#about-vartalap)
*   [Features](#features)
*   [Technologies Used](#technologies-used)
*   [Getting Started](#getting-started)
    *   [Prerequisites](#prerequisites)
    *   [Installation](#installation)
    *   [Configuration](#configuration)
    *   [Running the Application](#running-the-application)
*   [Usage](#usage)
*   [API Endpoints](#api-endpoints)
*   [Contributing](#contributing)
*   [License](#license)
*   [Contact](#contact)

---

## About VartaLap

VartaLap is a modern, real-time messaging application designed to provide a seamless communication experience, similar to popular platforms like WhatsApp. Built with a robust MERN (MongoDB, Express.js, React, Node.js) stack, VartaLap aims to offer a secure, scalable, and intuitive platform for instant messaging, group chats, and more.

This project is structured into two main parts: a `client` (frontend) built with React.js, and a `server` (backend) powered by Node.js and Express.js, utilizing WebSockets for real-time communication.

---

## Features

*   **User Authentication**: Secure user registration and login.
*   **Real-time Messaging**: Instant message delivery and reception using WebSockets.
*   **One-to-One Chat**: Private conversations between two users.
*   **Group Chat (Planned)**: Create and participate in group discussions.
*   **User Presence**: See which users are online/offline.
*   **Typing Indicators (Planned)**: Show when someone is typing.
*   **Message History**: Persistent chat history for all conversations.
*   **Responsive UI**: A user-friendly interface accessible across various devices.

---

## Technologies Used

VartaLap leverages a comprehensive set of modern web technologies to deliver its features:

**Client-Side (Frontend):**
*   **React.js**: A JavaScript library for building user interfaces.
*   **Vite**: A fast build tool for modern web projects.
*   **Tailwind CSS (or similar)**: For rapid UI development and styling.
*   **Axios**: For making HTTP requests to the backend.
*   **Socket.IO Client**: For real-time communication with the server.

**Server-Side (Backend):**
*   **Node.js**: A JavaScript runtime for server-side logic.
*   **Express.js**: A fast, unopinionated, minimalist web framework for Node.js.
*   **MongoDB**: A NoSQL document database for storing user data and messages.
*   **Mongoose**: An ODM (Object Data Modeling) library for MongoDB and Node.js.
*   **Socket.IO**: A library for real-time, bidirectional, event-based communication.
*   **JWT (JSON Web Tokens)**: For secure user authentication.
*   **Bcrypt.js**: For password hashing.
*   **dotenv**: For managing environment variables.

---

## Getting Started

Follow these instructions to set up and run VartaLap on your local machine for development and testing purposes.

### Prerequisites

Before you begin, ensure you have the following installed:

*   **Node.js**: Version 14.x or higher. You can download it from [nodejs.org](https://nodejs.org/).
*   **npm** (Node Package Manager) or **Yarn**: Comes bundled with Node.js, or install Yarn separately.
*   **MongoDB**: A running MongoDB instance. You can install it locally, use Docker, or a cloud service like MongoDB Atlas.

### Installation

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/daivik-hirpara/VartaLap.git
    cd VartaLap
    ```

2.  **Install server dependencies:**

    ```bash
    cd server
    npm install # or yarn install
    ```

3.  **Install client dependencies:**

    ```bash
    cd ../client
    npm install 
    ```

### Configuration

Both the server and client require environment variables for proper functioning.

1.  **Server Configuration:**
    Create a `.env` file in the `server` directory and add the following variables:

    ```env
    PORT=5000
    MONGO_URI=mongodb://localhost:27017/vartalap_db
    JWT_SECRET=your_jwt_secret_key
    CLIENT_URL=http://localhost:3000
    ```
    *   `PORT`: The port on which the server will run.
    *   `MONGO_URI`: Your MongoDB connection string.
    *   `JWT_SECRET`: A strong, random string for JWT token encryption. Generate a complex one.
    *   `CLIENT_URL`: The URL of your frontend application.

2.  **Client Configuration:**
    Create a `.env` file in the `client` directory and add the following variables:

    ```env
    VITE_SERVER_URL=http://localhost:5000
    ```
    *   `VITE_SERVER_URL`: The URL of your backend server.

### Running the Application

1.  **Start the Server:**
    Navigate to the `server` directory and run:

    ```bash
    cd ../server
    npm start # or yarn start
    ```
    The server will typically run on `http://localhost:5000` (or the `PORT` you configured).

2.  **Start the Client:**
    Navigate to the `client` directory and run:

    ```bash
    cd ../client
    npm run dev # or yarn dev
    ```
    The client application will typically open in your browser at `http://localhost:3000` (or another port if 3000 is occupied).

---

## Usage

Once both the server and client are running:

1.  **Register a new account:** On the client application, navigate to the registration page and create a new user account.
2.  **Login:** Use your newly created credentials to log in.
3.  **Start Chatting:** Once logged in, you should see a list of available users. Click on a user to open a one-on-one chat and start sending messages in real-time.

---

## API Endpoints

The server provides a RESTful API for user management and messaging, alongside WebSocket communication for real-time features.

| Method | Endpoint                    | Description                                  |
| :----- | :-------------------------- | :------------------------------------------- |
| `POST` | `/api/auth/register`        | Register a new user                          |
| `POST` | `/api/auth/login`           | Authenticate user and get JWT token          |
| `GET`  | `/api/users`                | Get all registered users (requires auth)     |
| `GET`  | `/api/messages/:receiverId` | Get messages between current user and receiver (requires auth) |
| `POST` | `/api/messages`             | Send a new message (via REST, or directly via Socket.IO) |

**WebSocket Events (Socket.IO):**

*   `connection`: Fired when a client connects.
*   `disconnect`: Fired when a client disconnects.
*   `sendMessage`: Client sends a message to another user.
*   `receiveMessage`: Server broadcasts a new message to the intended recipient.
*   `userOnline`: Server broadcasts when a user comes online.
*   `userOffline`: Server broadcasts when a user goes offline.
*   `typing`: Client sends typing indicator.
*   `stopTyping`: Client stops typing.

---

## Contributing

We welcome contributions to VartaLap! If you'd like to contribute, please follow these steps:

1.  **Fork the repository.**
2.  **Create a new branch** for your feature or bug fix: `git checkout -b feature/your-feature-name` or `bugfix/fix-description`.
3.  **Make your changes.**
4.  **Commit your changes** with a clear and concise message: `git commit -m "feat: Add new feature"`.
5.  **Push your branch** to your forked repository: `git push origin feature/your-feature-name`.
6.  **Open a Pull Request** to the `main` branch of the original repository.

Please ensure your code adheres to the project's coding style and includes appropriate tests if applicable.

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

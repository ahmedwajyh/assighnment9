# Saraha App

A RESTful API backend for a Saraha-style anonymous messaging application, built with **Node.js**, **Express.js**, **MongoDB**, and **Mongoose**.

The project follows a modular and organized structure with authentication, user management, database repositories, error handling, password hashing, and phone-number encryption.

## 🚀 Technologies

* Node.js
* Express.js
* MongoDB
* Mongoose
* bcrypt
* Crypto
* dotenv
* ES Modules

## ✨ Features

* User Signup
* User Login
* Email uniqueness validation
* Password hashing using bcrypt
* Phone number encryption using AES-256-CBC
* Phone number decryption during login
* MongoDB database connection
* Mongoose schema and model
* Global error handling
* Custom application exceptions
* Modular project structure
* Development and production environment configuration

## 📁 Project Structure

```text
saraha-app-main/
│
├── config/
│   ├── .env.development
│   ├── .env.production
│   └── config.service.js
│
├── src/
│   ├── DB/
│   │   ├── connection.db.js
│   │   ├── index.js
│   │   └── model/
│   │       ├── index.js
│   │       └── user.model.js
│   │
│   ├── common/
│   │   ├── enum/
│   │   ├── exception/
│   │   ├── repository/
│   │   ├── security/
│   │   └── utils/
│   │
│   ├── middleware/
│   │   └── error.middleware.js
│   │
│   ├── modules/
│   │   ├── auth/
│   │   │   ├── auth.controller.js
│   │   │   ├── auth.service.js
│   │   │   └── index.js
│   │   │
│   │   └── user/
│   │       ├── user.controller.js
│   │       ├── user.service.js
│   │       └── index.js
│   │
│   └── main.js
│
├── .gitignore
├── package.json
└── package-lock.json
```

## 🔐 Authentication

### Signup

**POST**

```text
/auth/signup
```

Example request:

```json
{
  "userName": "Ahmed Wageeh",
  "email": "ahmed@example.com",
  "password": "12345678",
  "phone": "01000000000",
  "gender": 0,
  "DOB": "2004-01-01"
}
```

The password is securely hashed using **bcrypt** before being stored in the database.

The phone number is encrypted before being stored.

### Login

**POST**

```text
/auth/login
```

Example request:

```json
{
  "email": "ahmed@example.com",
  "password": "12345678"
}
```

The server verifies the password using bcrypt and decrypts the stored phone number after successful authentication.

## 👤 User Profile

### Get User Profile

**GET**

```text
/user/?id=USER_ID
```

Returns the requested user profile.

## 🗄️ Database

The application uses **MongoDB** with **Mongoose**.

The User model contains:

* First Name
* Last Name
* Email
* Password
* Date of Birth
* Phone
* Gender
* Profile Image
* Cover Images
* Confirmation Email Date
* Created At
* Updated At

### Gender

```text
Male   = 0
Female = 1
```

## 🔒 Security

### Password Hashing

Passwords are hashed using:

```text
bcrypt
```

Passwords are never stored as plain text.

### Phone Encryption

Phone numbers are encrypted using:

```text
AES-256-CBC
```

The encryption key and IV length are stored in environment variables.

## ⚙️ Environment Variables

Create environment files inside the `config` folder.

### `.env.development`

```env
PORT=7000
DB_URI=mongodb://127.0.0.1:27017/saraha
SALT=10
ENCRYPTION_KEY=your_32_byte_encryption_key
IVLENGTH=16
```

Do not upload your real encryption key or database credentials to GitHub.

## 📦 Installation

Clone the repository:

```bash
git clone <YOUR_REPOSITORY_URL>
```

Move into the project:

```bash
cd saraha-app-main
```

Install dependencies:

```bash
npm install
```

## ▶️ Running the Project

### Development

```bash
npm run start:dev
```

### Production

```bash
npm run start:prod
```

The server runs on:

```text
http://localhost:7000
```

## 🌐 API Endpoints

| Method | Endpoint            | Description       |
| ------ | ------------------- | ----------------- |
| GET    | `/`                 | Check server      |
| POST   | `/auth/signup`      | Create a new user |
| POST   | `/auth/login`       | Login user        |
| GET    | `/user/?id=USER_ID` | Get user profile  |

## 🧪 Testing

You can test the API using:

* Postman
* Thunder Client
* Insomnia

Example:

```text
POST http://localhost:7000/auth/signup
```

```text
POST http://localhost:7000/auth/login
```

## 🛠️ Error Handling

The project contains centralized error handling and custom exceptions such as:

* `ConflictException`
* `NotFoundException`
* `UnAuthorizedException`
* `ForbiddenException`
* `ApplicationException`

## 👨‍💻 Author

**Ahmed Wageeh**

Backend Developer | Node.js

## 📄 License

This project is for educational and development purposes.

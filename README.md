# 🔥 Full Stack Boilerplate - Flask + React + PostgreSQL

This is a simple and efficient full stack boilerplate designed for modern web development using **Flask (Python backend)**, **React (frontend)**, and **PostgreSQL**. It's ready to run locally or be deployed to a **VPS** using **Docker**.

## 📦 Tech Stack

- **Backend:** Flask + SQLAlchemy
- **Frontend:** React + Vite
- **Database:** PostgreSQL
- **Containerization:** Docker + Docker Compose

---

## 🚀 Getting Started Locally

> This setup assumes you already have Python, Node.js, and PostgreSQL installed on your system.

### 1. Set up environment variables

Create a `.env` file and set your backend URL:

```env
backend_url=http://localhost:5000
```

### 2. Backend Setup

```bash
pipenv shell
pipenv install
flask db init
pipenv run migrate
pipenv run upgrade
pipenv run start
```

### 3. Frontend Setup (in a new terminal)

```bash
npm install
npm run start
```

You can now develop and test the app on your PC locally. 🚧

---

## 🐳 Deploy to VPS with Docker

Make sure your Docker image is built and pushed to Docker Hub (or another container registry):

```bash
docker push fedesu/boilerplate-fullstack-4geeks:<tagname>
```

Then, on your VPS, simply run:

```bash
docker-compose up -d
```

This will pull the image and run it in the background, fully deployed. ✅

---

## 📁 Project Structure

```
.
├── src
│   ├── api         # Flask backend
│   ├── front       # React frontend
│   ├── models      # SQLAlchemy models
│   └── wsgi.py     # Application entry point
├── Dockerfile
├── docker-compose.yml
├── .env
└── README.md
```

---

## 👨‍💻 Author

Made with ❤️ by [Fede](https://github.com/fedesuarezdev)

# 🔥 Full Stack Boilerplate - Flask + React + PostgreSQL

This is a simple and efficient full stack boilerplate designed for modern web development using **Flask (Python backend)**, **React (frontend)** with flux architecture, and **PostgreSQL**. It's ready to run locally or be deployed to a **VPS** using **Docker**.

## 📦 Tech Stack

- **Backend:** Flask + SQLAlchemy
- **Frontend:** React + Webpack
- **Database:** PostgreSQL
- **Containerization:** Docker + Docker Compose

---

## 🚀 Getting Started Locally

> This setup assumes you already have Python, Node.js, and PostgreSQL installed on your system.

### 1. Set up environment variables

Create a `.env` file and set your backend URL, use de file called .env.example as an example (you can copy it and paste it and just change the name of it to .env):

### 2. Backend Setup

```bash
pipenv shell
pipenv install
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

Make sure you have pulled the image from Docker Hub (or another container registry):

```bash
docker push fedesu/boilerplate-fullstack-4geeks:<tagname>
```

Then, on your VPS, simply run:

## 📁 IMPORTANT

You must have a file called .env with all the env variables (as the .env.example) wherever you have your container in the VPS.
You also must have a docker-compose.yml in the same directory, like this one:

```docker-compose.yml
version: '3.8'

services:
  db:
    image: postgres:15
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: root
      POSTGRES_DB: example
    ports:
      - "5432:5432"
    volumes:
      - postgres-data:/var/lib/postgresql/data

  web:
    image: edesu/boilerplate-fullstack-4geeks:<tagname>
    ports:
      - "3001:3001"
    env_file:
      - .env
    depends_on:
      - db
    command: >
      sh -c "pipenv run flask db upgrade &&
             pipenv run gunicorn wsgi:application --chdir src --bind 0.0.0.0:3001"

volumes:
  postgres-data:
```

Once you created that file, run this command:

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

Made with ❤️ by [Fede](https://github.com/federico-serron) and 4Geeks
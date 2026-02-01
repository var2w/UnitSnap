# Local Setup Instructions for Windows 11

This guide will help you set up and run the UnitSnap application locally on your Windows 11 machine.

## Prerequisites

1.  **Node.js**: Install the latest LTS version of [Node.js](https://nodejs.org/).
2.  **PostgreSQL**: Install [PostgreSQL](https://www.postgresql.org/download/windows/) and ensure the service is running.
3.  **Git**: Install [Git for Windows](https://git-scm.com/download/win).

## Setup Steps

1.  **Clone the Repository**
    Open PowerShell or Command Prompt and run:
    ```bash
    git clone <your-repository-url>
    cd unit-converter-app
    ```

2.  **Install Dependencies**
    ```bash
    npm install
    ```

3.  **Environment Variables**
    Create a `.env` file in the root directory and add the following:
    ```env
    DATABASE_URL=postgresql://username:password@localhost:5432/unitsnap
    SESSION_SECRET=your_random_secret_here
    AI_INTEGRATIONS_OPENAI_API_KEY=your_openai_api_key
    ```
    *Replace `username`, `password`, and `your_openai_api_key` with your actual credentials.*

4.  **Database Setup**
    Create a database named `unitsnap` in your PostgreSQL instance, then push the schema:
    ```bash
    npm run db:push
    ```

5.  **Run the Application**
    ```bash
    npm run dev
    ```
    The application will be available at `http://localhost:5000`.

## Notes for Windows 11
- If you encounter permission issues, try running your terminal as Administrator.
- Ensure that port 5000 is not being used by another application.
- For AI features, you must provide a valid OpenAI API key in the `.env` file.

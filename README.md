# Mario Mimic

Mario Mimic is a TypeScript-based application designed to mimic the gameplay style and mechanics of classic Mario games. This project demonstrates interactive game logic, asset management, and modern deployment workflows using Docker and Google Cloud.

## Features

- Classic Mario-inspired gameplay mechanics
- Modular TypeScript codebase for easy maintenance and scalability
- Containerized with Docker for consistent local and cloud deployments
- Ready for deployment on Google Cloud Run

## Technical Details

Mario Mimic is architected as a browser-based game using TypeScript, HTML5 Canvas, and modern web technologies. Its core technical features include:

- **Rendering:** The game uses a custom `GameRenderer` class that draws pixel-art style sprites (Mario, Goombas, coins, etc.) directly onto the HTML5 Canvas. Sprites are rendered using colored rectangles to simulate classic 8-bit graphics, including simple animation effects.
- **Entities:** The game world is made up of several types of entities, such as `Player`, `Enemy` (like Goombas), `Coin`, and `Platform`. Each entity manages its own state (position, animation, etc.) and is updated every frame.
- **Game Loop:** The main logic is handled in the `Game` class, which initializes levels, manages the player, enemies, and coins, handles collision detection, and updates the game state on every animation frame.
- **Input Handling:** Keyboard input (arrow keys for movement, spacebar for jumping) is managed by an `InputHandler` class, providing responsive gameplay.
- **Physics & Collision:** Collision detection ensures Mario interacts correctly with platforms, coins, and enemies, mimicking classic platformer challenges.
- **Level Design:** Levels are initialized programmatically with arrays of `Platform`, `Enemy`, and `Coin` objects, enabling flexible and extensible level design.
- **UI:** The UI displays score, lives, and level, and includes a game-over screen with restart capability.
- **Styling:** The game features a retro aesthetic with pixel-perfect scaling and color schemes styled via CSS.

## Prerequisites

- [Node.js](https://nodejs.org/) (v16 or higher)
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)
- [Docker](https://www.docker.com/get-started) (for cloud deployment or local container testing)
- (For Google Cloud) [Google Cloud SDK](https://cloud.google.com/sdk/docs/install) installed and initialized
- A Google Cloud Project with billing enabled

## Local Installation and Running

1. **Clone the Repository**
    ```bash
    git clone https://github.com/chidhvilaskacham/mario-mimic.git
    cd mario-mimic
    ```

2. **Install Dependencies**
    ```bash
    npm install
    # or
    yarn install
    ```

3. **Build the Project**
    ```bash
    npm run build
    # or
    yarn build
    ```

4. **Run the Application Locally**
    ```bash
    npm start
    # or
    yarn start
    ```
   The application should now be running at `http://localhost:3000` (or another configured port).

## Running Locally with Docker

1. **Build the Docker Image**
    ```bash
    docker build -t mario-mimic .
    ```

2. **Run the Docker Container**
    ```bash
    docker run -p 8080:8080 mario-mimic
    ```
    - The application should now be accessible at `http://localhost:8080`.

> **Note:** Make sure your application code listens on the port defined by the `PORT` environment variable for compatibility with cloud platforms.

## Deploying on Google Cloud Run

1. **Authenticate with Google Cloud**
    ```bash
    gcloud auth login
    gcloud config set project YOUR_PROJECT_ID
    ```

2. **Build and Push the Docker Image**
    ```bash
    gcloud builds submit --tag gcr.io/$(gcloud config get-value project)/mario-mimic
    ```

3. **Deploy to Cloud Run**
    ```bash
    gcloud run deploy mario-mimic \
        --image gcr.io/$(gcloud config get-value project)/mario-mimic \
        --platform managed --region us-central1 --allow-unauthenticated
    ```

4. **Access the Application**
    - After successful deployment, Google Cloud will provide a public URL for your Mario Mimic application.

## Project Structure

- `src/` - Main source code (TypeScript)
- `Dockerfile` - Container build instructions
- `package.json` - Project metadata and scripts

<img width="1536" height="1024" alt="mario1" src="https://github.com/user-attachments/assets/b9947265-6682-4e4a-894c-58c268e709fe" />
<img width="1024" height="1536" alt="mario2" src="https://github.com/user-attachments/assets/272e76f6-6a01-43a9-8a32-eda5e0272ffe" />


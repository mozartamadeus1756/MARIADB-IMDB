# IMDB - by kine !

I've made a IMDB copy-project, where you can find movies to watch ect !! This projeck is made using svelte as my frontend and bakcend, whilst i am using mairadb as my database. 

this website is made for people looking for more movies to watch, or just want somehtign random playing in the background. you can randomise a movie or search for anthing. as someone who has trouble or struggle to find something to watch, this website is perfect !! 

- [IMDB project](#IMDB-project)
  - [Prerequisits](#prerequisits)
  - [How to run??](#how-to-run-)
  - [Other](#other)

### Prerequisites
To run and use my application on your own you will need a few prerequisites.

To download and use different commands you'll need brew and node.js. **Brew** first:


```bash
# brew install
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

And so **node.js:**
```bash
# nvm install (to install node)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
```

```bash
# node install
nvm install 22
```

To add and manage passwords you'll need a database, you can decide on what to use, but im using **mariadb**, and this is how you install it:

```bash
# mariadb install 
brew install mariadb
```

Now, in your database of choice, you want to make this required table for the login and register pages to function:

```sql
-- Users table
CREATE TABLE users (
    user_id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(255),
    email VARCHAR(255),
    password BLOB
);
```

This is where our registered users are placed, and the passwords are crypted and secured. 

For our database to be secured, but also make a connection we'll make a `.env` file in our root directory, where we store our database credentials. 

**(change the values to what matches your own credentials)**

```env
DB_HOST=localhost
DB_USER=your_username
DB_PASSWORD=your_password
DB_NAME=your_database_name
DB_CONNECTION_LIMIT=5
```

## How to run ?? 

So now that you've downloaded the prerequisites, its time to run our app. 

First, you want to install npm (node) dependencies: 

```bash
npm install 
```
Also, too make the passwords register crypted, we also need to install **bcrypt****:

```bash
# install bcrypt
npm install bcrypt
```

And start the development server:

```bash
npm run dev 
```

**BTW** this is how all my folders and files look like: 

```src
IMDB/
├── src/
│   ├── lib/
│   │   ├── db/
│   │   │   └── mariadb.js     
│   └── routes/
│       ├── +page.svelte                    # Homepage
│       ├── db/
│       │    ├── login/
│       │    │   └── +server.js             # Login API
│       │    ├── register/
│       │    │   └── +server.js             # Register API
│       │    └── favorites/
│       │         ├── add/+server.js        # Add favorite
│       │         ├── remove/+server.js     # Remove favorite
│       │         ├── check/+server.js      # Check favorite
│       │         └── get/+server.js        # Get favorites
│       ├── components/
│       │   ├── MovieCard.svelte            # Movie display component
│       │   ├── Navbar.svelte               # Navigation
│       │   └── NavbarFav.svelte            # Navigation with favorites
│       ├── favorites/
│       │   └── +page.svelte                # Favorites page
│       ├── login/
│       │   └── +page.svelte                # Login page
│       ├── register/
│       │   └── +page.svelte                # Register page
│       ├── main/
│       │   └── +page.svelte                # Main movies page
│       ├── search/
│       │   └── +page.svelte                # Search page
│       └── randomise/
│           └── +page.svelte                # Random movie page
├── static/
│   └── movies.json                         # Movie data
├── package.json                            # Dependencies
├── .env 
└── README.md                               # Documentation
```

## Other 

To show how my project is built i've made a system sketch: 

```mermaid
graph TD
    %% User Layer
    A[USER<br/>Web Browser<br/>Search, Login, Favorites] --> B

    %% Frontend Layer
    B[FRONTEND - Svelte<br/>User Interface] --> C1[Login/Register<br/>Pages]
    B --> C2[Movie Search<br/>Component]
    B --> C3[Movie Display<br/>Component]
    B --> C4[Favorites<br/>Page]
    B --> C5[Random Movie<br/>Button]

    %% Backend connections
    C1 --> D[BACKEND<br/>Svelte + Node.js<br/>Server Logic]
    C2 --> D
    C3 --> D
    C4 --> D
    C5 --> D

    %% Backend services
    D --> E1[User Authentication<br/>Login/Register Logic]
    D --> E2[Movie API<br/>Get Movie Data]
    D --> E3[Search Logic<br/>Filter Movies]
    D --> E4[Favorites API<br/>Save/Remove Favorites]
    D --> E5[Random Logic<br/>Pick Random Movie]

    %% Data Layer
    E1 --> F1[DATABASE<br/>MariaDB]
    E4 --> F1
    
    E2 --> F2[MOVIE DATA<br/>movies.json]
    E3 --> F2
    E5 --> F2

    %% Database tables
    F1 --> G1[Users Table<br/>user_id, username, email, password]
    F1 --> G2[Favorites Table<br/>user_id, movie_id, title]

    %% Movie data details
    F2 --> H1[Movie Information<br/>title, genre, director<br/>year, rating, poster]

    %% Styling
    classDef userLayer fill:#3498db,stroke:#2980b9,stroke-width:2px,color:#fff
    classDef frontendLayer fill:#e74c3c,stroke:#c0392b,stroke-width:2px,color:#fff
    classDef backendLayer fill:#27ae60,stroke:#229954,stroke-width:2px,color:#fff
    classDef dataLayer fill:#9b59b6,stroke:#8e44ad,stroke-width:2px,color:#fff
    classDef fileLayer fill:#f39c12,stroke:#e67e22,stroke-width:2px,color:#fff

    class A userLayer
    class B,C1,C2,C3,C4,C5 frontendLayer
    class D,E1,E2,E3,E4,E5 backendLayer
    class F1,G1,G2 dataLayer
    class F2,H1 fileLayer
```

Later, for deployment i've made this risk anlalysis of my website, in case anything goes worng or i get attacked so and so ..











# sv

Everything you need to build a Svelte project, powered by [`sv`](https://github.com/sveltejs/cli).

## Creating a project

If you're seeing this, you've probably already done this step. Congrats!

```bash
# create a new project in the current directory
npx sv create

# create a new project in my-app
npx sv create my-app
```

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```bash
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```bash
npm run build
```

You can preview the production build with `npm run preview`.

> To deploy your app, you may need to install an [adapter](https://svelte.dev/docs/kit/adapters) for your target environment.
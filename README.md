Frontend side for face-recognition app that consists of 3 parts:

1. backend for user login/signin [here](https://github.com/aziret/smart-brain-api)
2. frontend for login/signing and using Clarifai's face-detection API (this app)
3. DB for saving users

## How to start:

NOTE: Following 1-2 steps are copied from the backend repo. So if you followed these steps in the backend repo, then no need to run them again. The frontend app was designed the way that backend API is running on port 3000, so ideally start backend app first, or run it explicitly on port 3000 or change the logic on frontend side to use the corresponding port.

1. Create a db for storing user data, e.g. createdb 'smart-brain' -> psql 'smart-brain'
2. Create the following tables in your DB:

- The queries here are from postgres console:

```
CREATE TABLE users (
    id serial PRIMARY KEY,
    name VARCHAR(100),
    email text UNIQUE NOT NULL,
    entries BIGINT DEFAULT 0,
    joined TIMESTAMP NOT NULL
);

CREATE TABLE login (
    id serial PRIMARY KEY,
    hash VARCHAR(100) NOT NULL,
    email text UNIQUE NOT NULL
);
```

3. Install packages from npm registry: npm install
4. Fill in env variables in .env file, e.g.:
   all the env variables are taken from Clarifai

```
REACT_APP_PAT= PAT
REACT_APP_USER_ID=USER_ID
REACT_APP_APP_ID=APP_ID
REACT_APP_MODEL_ID=MODEL_ID
REACT_APP_MODEL_VERSION_ID=VERSION_ID
```

5. Start the server: npm start

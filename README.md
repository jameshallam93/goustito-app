# goustisto-app

This is the final repo for the goustito recipe bank application, which makes use of submodules for the frontend and server.

The app currently supports user account creation, login/logout, searching for recipes via search terms and meal types (breakfast, lunch etc.), and saving recipes to the user vault.

## Requirements:

* Nodejs
* Docker with docker-compose
* An Atlas mongodb account with initialised cluster (see envinronment variables below)

Environment variables:
* REACT_APP_GOUSTITO_FRONTEND_PORT (configured to 3000)
* GOUSTITO_SERVER_PORT (configured to 3001)
* GOUSTITO_SERVER_MONGO_DB_URI (set up cluster at https://cloud.mongodb.com/ and follow connection instructions)
* GOUSTITO_SERVER_TOKEN_SECRET (configured to a random MD5 hash, but can be anything)
* REACT_APP_GOUSTITO_FRONTEND_API_ID (set up account at https://developer.edamam.com/ using their recipe API)
* REACT_APP_GOUSTITO_FRONTEND_EDAMAM_API_KEY (as above)


## Usage:

```
# clone repository and submodules
git clone --recurse-submodules https://github.com/jameshallam93/goustito-app

# install dependencies
npm install

# build server image
cd goustitoserver
docker build --file=dockerfile -t goustito-server .

# build frontend image
cd ..
cd goustito
docker build --file=dockerfile -t goustito-frontend .

# return to root directory and run docker compose
cd ..
docker-compose up
```

## Roadmap:

* I would like to add the ability to search by numerous different categories (i.e. calories, free-from etc.)
* I would like to set up a "social food feed", whereby users can pin one recipe each, and the feed displays a semi-curated list of recipes from pinned user recipes.





# goustisto-app

This is the final repo for the goustito recipe bank application, which makes use of submodules for the frontend and server.

An app for discovering and saving new recipes. It makes use of the EDAMAM recipe API, and allows users to save recipes to their vault.

Recipes can currently be searched for via search terms and meal types (breakfast, lunch, dinner etc.). However, in time I would like to make better use of the API, as it is also possible to search by calory content/ free-from labels.

Eventually, it could be used for in depth meal planning for those with particular dietary requirements.

This was desinged purely for the Gousto application and accordingly, the style sheets are influenced heavily by the Gousto branding. I have no intention to release this commercialy or otherwise, and it is entirely intended as a portfolio project.

The app currently supports user account creation, login/logout, searching for recipes via search terms and meal types (breakfast, lunch etc.), and saving recipes to the user vault.

## Requirements:

* Nodejs
* Docker with docker-compose
* An Atlas mongodb account with initialised cluster (see envinronment variables below)

Environment variables:
* REACT_APP_GOUSTITO_FRONTEND_PORT (configured to 3000)
* GOUSTITO_SERVER_PORT (configured to 3001)
* GOUSTITO_SERVER_MONGO_DB_URI (set up cluster at https://cloud.mongodb.com/ and follow connection instructions)
* (optional) GOUSTITO_SERVER_TEST_MONGO_DB_URI for running tests in a testing database, avoids messing up user data.
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
* I would like to be able to use docker-compose build instead of navigating individually to the directories and building (currently impossible with the bcrypt package I am using)

### [Change log](https://github.com/jameshallam93/goustito/blob/76b133ea55b9a22c865929c9b47948c6ee5366f6/ChangeLog.md)




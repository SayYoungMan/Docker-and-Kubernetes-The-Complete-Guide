# Building a Multi-Container Application

## Single Container Deployment Issues
- The app was simple - no dependencies
- Out image was built multiple times

## Application Overview
- Going to build complicated multi-container fibonacci calculator
- For index get the fibonacci sequence value
- Store the history and show on the webpage

## Application Architecture
- nginx server will do the routing, so it will route the request either to React server and Express server based on the client
- The values history will be stored in the Postgres database and calculated values will be stored in Redis
- Backend Express server will store the number permanently in Postgres and as key value pairs in Redis
- Worker will watch redis for new indicies, calculate new value and put it back to redis

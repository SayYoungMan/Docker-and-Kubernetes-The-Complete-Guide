# "Dockerizing" Multiple Services

- The source codes were copied from Chapter 8
- This Chapter aims to make docker files to them

## Nginx Path Routing
- Nginx is responsible to look for the request url starts with either '/' or '/api' in order to differentiate where the need to be routed to.
- This is better than setting different port for different servers because the port might change.
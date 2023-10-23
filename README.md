# paybank-documentation

### ⚡️ Overview

- Project created to document the PAYBANK project APIs;
- This project is using swagger;
- TThis is an apis documentation project referring to a project/study in partnership

All you need to do is edit the swagger spec, save as openapi.yml, and restart docker. Voila, UI and the mock API server are updated.

### 🐳 How to Run

```
docker-compose up -d

It will look like this.
docker-compose ps
         Name                       Command               State           Ports
----------------------------------------------------------------------------------------
swagger-api      /usr/local/bin/apisprout / ...   Up      0.0.0.0:8083->8000/tcp
swagger-editor   sh /usr/share/nginx/docker ...   Up      0.0.0.0:8081->8080/tcp
swagger-nginx    nginx -g daemon off;             Up      80/tcp, 0.0.0.0:8084->8084/tcp
swagger-ui       sh /usr/share/nginx/docker ...   Up      0.0.0.0:8082->8080/tcp
```

### 💻 How to Use

1. Edit swagger spec with swagger-editor
2. Save swagger spec as yaml from swagger-editor File menu
3. Move and save the yaml file as `swagger/openapi.yaml`
4. Execute `docker-compose restart` and swagger-ui and swagger-api(mock server) will be updated
5. If you want to read an external openapi.yaml file, import the file from swagger-editor `File > Import File` menu.

### 🚨 Heads-up

- When the UI is referenced as `http://localhost:8082/`, cache might be used even the changes are made in swagger files. So it may be better to refference as `http://127.0.0.1:8082/`(api, too.)
- When swagger-api failed to run, it's likely that api server failed to run because the openapi.json was not properly read. So use `docker logs` command and get rid of the cause then restart it again.
- If you want to access swagger-api from other domains(CORS), access swagger-api through swagger-nginx.

### 🚀 Swagger-editor

- Can edit swagger spec
- Can export swagger spec as json, yaml and etc. swagger-ui can read the files and they can be beautifly referenced as documentation. apisprout can read the yml and json then it can serve the mock API.

### 🚀 Swagger-ui

- Can referrence the documentation from swagger spec.
- swagger spec can be assined from yaml file path or API_URL path.

```
environment:
  SWAGGER_YAML: /openapi.yaml
  # API_URL: ""
```

- ./swagger/openapi.yaml is refferenced in this repository

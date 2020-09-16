# Jenkins-pipeline-scripts
jenkins pipeline script templates

# Reload jcasc configuration inside pod
```bash
curl -v -X POST "localhost:8080/reload-configuration-as-code/?casc-reload-token=$POD_NAME"
```

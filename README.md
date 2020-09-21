# Jenkins-pipeline-scripts
jenkins pipeline script templates

# Reload jcasc configuration inside pod
```bash
curl -v -X POST "localhost:8080/reload-configuration-as-code/?casc-reload-token=$POD_NAME"
```


## Docker
pull latest lts image
```bash
docker pull jenkins/jenkins:lts
```
Run Jenkins container in the background.
```bash
docker container run -d \
 --group-add $(stat -c '%g' /var/run/docker.sock) \
 -p 8080:8080 \
 -p 5000:5000 \
 -v /var/run/docker.sock:/var/run/docker.sock \
 -v jenkin-datas:/var/jenkins_home \
 -e JENKINS_OPTS="--prefix=/jenkins" \
 lazybuilds/jenkins:lts
 
```
*Note*: `--prefix=/jenkins` is used so that we can use it with any existing ingress to save cost on LB.

### Set timezone: (will be lost on restart)
```groovy
System.setProperty('org.apache.commons.jelly.tags.fmt.timeZone', 'Asia/Kolkata')
```
---

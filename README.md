# Katalon Tests in Docker and Jenkins Pipeline

## Obtain key

Katalon API key is in your TestOps - <https://analytics.katalon.com/user/apikey>

## Run Docker Container

```
docker run -t --rm -v "$(pwd)":/tmp/project katalonstudio/katalon \
    katalonc.sh -projectPath=/tmp/project \
    -browserType="Chrome" -retry=0 -statusDelay=15 \
    -testSuitePath="Test Suites/login" \
    -apikey="YOUR KEY"
```

## Run in Jenkins Pipeline

Set your Katalon API key in http://localhost:8080/credentials/ as Secret Text. See line 10 in Jenkinsfile.

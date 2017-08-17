# Tips and Links concerning SonarQube

# Analyze Mave Project including coverage
```bash
$> mvn clean org.jacoco:jacoco-maven-plugin:0.7.9:prepare-agent \
        install \
        sonar:sonar \
        -Dsonar.host.url=http://127.0.0.1:9000
```

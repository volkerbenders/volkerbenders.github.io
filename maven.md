# My Maven Notebook


## Dependencies

### Generating an Image of all dependencies
```bash
  mvn org.fusesource.mvnplugins:maven-graph-plugin:reactor -Dhide-external=true
```
Generates a png image file in your projects target folder

## Deployment

### To Nexus
* [Baeldung: Deploy 2 Nexus](http://www.baeldung.com/maven-deploy-nexus)
```bash
$> mvn clean deploy -Dmaven.test.skip=true
```

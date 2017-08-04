# My Maven Notebook

## Depenencies

### Generating an Image of all dependencies
```bash
  mvn org.fusesource.mvnplugins:maven-graph-plugin:reactor -Dhide-external=true
```
Generates a png image file in your projects target folder

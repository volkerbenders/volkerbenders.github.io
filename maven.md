# My Maven Notebook


## Dependencies

### Generating an Image of all dependencies
```bash
  mvn org.fusesource.mvnplugins:maven-graph-plugin:reactor -Dhide-external=true
```
Generates a png image file in your projects target folder

[Discussion on generating dependency-graphs](https://stackoverflow.com/questions/4084669/how-to-generate-a-graph-of-the-dependency-between-all-modules-of-a-maven-project)

### the script i cuurently use
```bash
#!/bi/sh
HIDE_EXTERNAL=false
PROJECT=ebp-reactor/vrbankenportal
TIMESTAMP=$(date +"%D_%H-%M")
echo TIME: $TIMESTAMP
POM=ebp-reactor/pom.xml
POM=$PROJECT/pom.xml
label="@JavaVolker"
#echo \
mvn -f $POM \
	org.fusesource.mvnplugins:maven-graph-plugin:reactor	\
	 -Dhide-external=$HIDE_EXTERNAL

convert $PROJECT/target/reactor-graph.png -background Khaki \
 label:"by $label" \
 -size 5 \
 -gravity center \
 -append $PROJECT/target/dependencies.png
```
## Deployment

### To Nexus
* [Baeldung: Deploy 2 Nexus](http://www.baeldung.com/maven-deploy-nexus)
```bash
$> mvn clean deploy -Dmaven.test.skip=true
```

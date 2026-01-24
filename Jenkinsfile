pipeline {
agent any
environment {
// Set JAVA_HOME to the path of your Java 17 installation
JAVA_HOME = 'C:\Program Files\Java\jdk-21.0.10'
// Add Java bin directory to PATH
PATH = "${JAVA_HOME}\\bin;${env.PATH}"
}
tools {
maven 'maven3'
}
stages {
stage('GetCode') {
steps {
git branch: 'main', url: 'https://github.com/mgidw/test.git'
}
}
stage('SonarQube analysis') {
steps {
withSonarQubeEnv('SonarQubeserver') {
bat script: """
sonar-scanner -D"sonar.projectKey=Devops" \
-D"sonar.sources=." \
-D"sonar.host.url=http://localhost:9000" \
-D"sonar.login=sqa_5724e67e9fa2d5b71ea0304d96fa4fc13484ff59"
"""
}
}
}
}
}

pipeline {
agent any
tools {
maven 'maven'
}
stages {
stage('Git Checkout') {
steps {
git branch: 'main',
credentialsId: 'b43c15d0-7df1-4e0c-bd5e-d0ca7a287179',
url: 'https://github.com/navneetguraya/sonar.git'
}
}
stage ('build') {
steps {
sh 'mvn clean'
}
}
stage ('Compile') {
steps {
sh 'mvn compile'
}
}
stage('Test') {
steps {
sh 'mvn test'
}
}
stage ('Package') { 
steps {
sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
}
}
stage ('Deploy War File') {
steps {
sh "mvn sonar:sonar"
}
}
}
}

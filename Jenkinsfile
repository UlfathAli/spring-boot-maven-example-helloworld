pipeline {
    agent any
    tools {
        withMaven {
        maven 'apache-maven-3.5.4' 
    }
    stages {
        stage('Example') {
            steps {
                withMaven {
                sh 'mvn --version'
            }
        }
    }
}

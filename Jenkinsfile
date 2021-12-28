pipeline {
    agent any

    tools{
       maven 'localmaven' 
    }
    stages {
        stage('Build') { 
            steps {
               sh 'mvn clean package' 
            }
            post {
               success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.jar'
                   }
              } 
          }


    stage('Deliver') {
        steps {
             sh 'scp -v -o StrictHostKeyChecking=no  -i /var/lib/jenkins/secrets/mykey target/*.jar testjenkins@157.175.72.119:/home'
             sh "sshpass -p password ssh -o StrictHostKeyChecking=no -i /var/lib/jenkins/secrets/mykey testjenkins@157.175.72.119:/home"
        }
    }
}

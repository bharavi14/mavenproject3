pipeline {
    agent any
    stages {
        stage('MVN Build') {
             steps{
                 echo "Building Jar File..............."
                 sh "mvn clean install"
            }
            post {
                success {
                    echo "Archiving Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy War To Tomcat Server') { 
            steps {
                deploy adapters: [tomcat7(credentialsId: 'tomcat', path: '', url: 'http://13.127.141.71:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}

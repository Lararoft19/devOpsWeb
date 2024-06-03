pipeline{
    agent any
    tools {
        maven 'local_maven'
    }
    stages{
        stage ('Build') {
            steps{
                bat 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps {
               deploy adapters: [tomcat7(credentialsId: '99306f68-2bc0-4bc7-9550-363f9e71e599', path: '', url: 'http://localhost:8181/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}

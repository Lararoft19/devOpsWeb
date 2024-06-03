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
              deploy adapters: [tomcat7(credentialsId: 'adad82fb-0c72-4be4-9219-380752e9eafb', path: '', url: 'http://localhost:8181/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}

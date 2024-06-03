pipeline{
    agent any

    stages{
        stage ('Build') {
            steps{
                sh 'mvn clean package'
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
                deploy adapters: [tomcat7(credentialsId: 'e228f11b-8ed7-417f-9897-42f61d5f7e20', path: '', url: 'http://localhost:8181/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}

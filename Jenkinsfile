pipeline{
    agent any
    
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post {
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
                deploy adapters: [tomcat9(credentialsId: 'apachcat', path: '', url: 'http://3.80.66.193:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}

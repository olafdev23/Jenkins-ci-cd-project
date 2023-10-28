pipeline{
    agent any
    tools{
        maven 'MAVEN_HOME'
    }
    stages{
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post {
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/WebAppCal-0.0.6.war'
                }
            }
        }
        stage ('Deploy to tomcat server') {
            steps{
              deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://3.137.174.204:8080/')], contextPath: null, war: '**/target/WebAppCal-0.0.6.war'
            }
        }
    }
}

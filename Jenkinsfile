node {
    
    stage('clone Repo') {
        git credentialsId: 'github', url: 'https://github.com/olafdev23/Jenkins-ci-cd-project.git'
    }
    
    stage('Maven Build'){
        sh 'mvn clean package'
    }
    stage('Deploy'){
        sshagent(['Tomcat-Server-Agent']) {
            sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@3.91.202.71:/home/ec2-user/apache-tomcat-9.0.82/webapps'
        }
    }
}

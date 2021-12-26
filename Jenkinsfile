pipeline{
    agent any
    environment {
        PATH = "/opt/maven/bin/:$PATH"
    }
    stages{
        stage('clone code'){
            steps{
                git branch: 'main', credentialsId: 'e08d4ed4-3328-4708-ab0b-14275d1e9355', url: 'https://github.com/Deekshitha-R07/WebApp.git'
            }
        }
        stage('build'){
            steps{
               sh 'mvn clean install'
            }
        }
        stage('deploy'){
            steps{
              sshagent(['deploy_user']) {
                    sh 'scp target/moa.war ec2-user@13.233.111.135:/opt/tomcAt/webapps'

                }
            }
        }
    }
}

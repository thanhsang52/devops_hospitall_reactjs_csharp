pipeline {
    agent any
    environment {
        SSH_IP = "146.190.108.212"
        DEPLOY_PATH = "/var/www/html"
    }
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('List files') {
            steps {
                sh "ls -la"
            }
        }
        stage('hello') {
            steps{
                withCredentials([
                    //usernamePassword(credentialsId:'github-login',usernameVariable:'USER_GIT', passwordVariable:'PASS_GIT'),
                    sshUserPrivateKey(credentialsId:'ssh-key', keyFileVariable:'SSH_KEY', usernameVariable:'SSH_USER')   
                ]){
                    sh """
                        ssh -o StrictHostKeyChecking=no -i ${SSH_KEY} ${SSH_USER} '
                            cd ${DEPLOY_PATH} && git pull
                            docker-compose down
                            docker-compose build
                            docker-compose up -d
                        '
                    """
                }      
           }        
       }    
    }
}

pipeline {
    agent any

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
                    sshUserPrivateKey(credentialsId:'ssh-key', keyFileVariable:'TOKEN', usernameVariable:"USER")   
                ]){
                    echo " ${USER} ${TOKEN} "
                }      
           }        
       }    
    }
}

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
    }
}

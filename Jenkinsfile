pipeline {
    agent any
    
    environment {
        PATH = '$PATH:/usr/local/Cellar/maven/3.5.3/libexec/bin'
    }

    stages {
        stage('Build') {
          steps {
                sh 'mvn package'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}

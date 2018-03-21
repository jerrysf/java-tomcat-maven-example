pipeline {
    agent any

    stages {
        stage ('Clone') {
        	checkout scm
        }
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

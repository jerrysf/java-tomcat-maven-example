pipeline {
    agent any
    
    environment {
        MAVEN_HOME = '/usr/local/Cellar/maven/3.5.3/libexec/bin'
    }

    stages {
        stage('Build') {
          steps {
              sh '${MAVEN_HOME}/bin/mvn package'
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

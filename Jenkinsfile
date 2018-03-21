pipeline {
    agent any
    
    environment {
        MAVEN_HOME = '/usr/local/Cellar/maven/3.5.3/libexec'
    }

    stages {
        stage('Build') {
          steps {
              sh '${MAVEN_HOME}/bin/mvn package'
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying..'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying..'
            }
        }
        
        
    }
}

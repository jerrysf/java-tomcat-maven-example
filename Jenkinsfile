pipeline {
    agent any
    
    environment {
        MAVEN_HOME = '/usr/local/Cellar/maven/3.5.3/libexec'
    }

    stages {
        stage('Build') {
          steps {
              sh '${MAVEN_HOME}/bin/mvn package'
              archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                sh '/usr/local/bin/ansible-playbook -i hosts staging.yml'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        
        stage('Deploy to Production') {
            steps {
                sh '/usr/local/bin/ansible-playbook -i hosts production.yml'
            }
        }
        
        
    }
}

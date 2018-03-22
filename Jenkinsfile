pipeline {
    agent any

    environment {
        MAVEN_HOME = '/usr/local/Cellar/maven/3.5.3/libexec'
    }

    stages {
        agent {
                label 'build'
            }
        stage('Build') {
          steps {
              sh '${MAVEN_HOME}/bin/mvn package'
              archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
            }
        }

        agent {
                label 'deploy'
            }
        stage('Deploy to Staging') {
            steps {
                sh 'ansible-playbook -i hosts staging.yml --extra-vars "build_id=${env.BUILD_ID}"'
            }
        }

        agent {
                label 'test'
            }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }

        agent {
                label 'deploy'
            }
        stage('Deploy to Production') {
            steps {
                sh 'ansible-playbook -i hosts production.yml --extra-vars "build_id=${env.BUILD_ID}"'
            }
        }

        post {
        failure {
            mail to: team@example.com, subject: 'The Pipeline failed, please take actions!'
        }
    }
    }
}

//=========================================================================
//   Homework Jenkinsfile
//   Author: Jerry Yu
//   Email: jerrysf2009@gmail.com
//   Created: 2018-03-21
//=========================================================================

pipeline {
    agent any

    environment {
        MAVEN_HOME = '/usr/local/Cellar/maven/3.5.3/libexec'
        ANSIBLE_HOME = '/usr/local/Cellar/ansible/2.4.3.0_4'
    }

    stages {
        
        stage('Build') {
          agent {
                label 'build'
            }
          steps {
              sh '${MAVEN_HOME}/bin/mvn package'
              archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
            }
        }

        
        stage('Deploy to Staging') {
            agent {
                label 'deploy'
            }
            steps {
                sh "${ANSIBLE_HOME}/bin/ansible-playbook -i hosts staging.yml --extra-vars build_id=${env.BUILD_ID}"
            }
        }

        
        stage('Test') {
            agent {
                label 'test'
            }
            steps {
                echo 'Testing..'
            }
        }

        
        stage('Deploy to Production') {
            agent {
                label 'deploy'
            }
            steps {
                sh "${ANSIBLE_HOME}/bin/ansible-playbook -i hosts production.yml --extra-vars build_id=${env.BUILD_ID}"
            }
        }
    }

        post {
            failure {
            emailext (
               subject: "Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' failed",
               body: "Please check and fix the failure!",
               from: "jenkins@company.com",
               to: "developers@company.com"
              )
        }
    }
    
}

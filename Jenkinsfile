pipeline {
     agent { label 'jenkinslave' }
     stages {
          stage("clone code") {
               steps {
                    git 'https://github.com/datsys96/nodejs11-04hw-github.git'
               }
          }
          stage("build image") {
               steps {
                    sh 'docker build -t datsys96/nodejs1104github1 .'
               }
          }
        stage('Push Image to dockerhub') {
            steps {
                withDockerRegistry(credentialsId: 'datsys96', url: 'https://index.docker.io/v1/') {
                sh 'docker push datsys96/nodejs1104github1:latest'
                }
            }
     }

    post {
        always {
	emailext body: 'helle day la jenkin nha', subject: 'test jenkin', to: 'datbeo12c@gmail.com'
        }
	        success {
            emailext body: 'ok ${DEFAULT_SUBJECT}', subject: '${DEFAULT_CONTENT}', to: 'datbeo12c@gmail.com'
        }
        unstable {
            emailext body: 'unstable ${DEFAULT_SUBJECT}', subject: '${DEFAULT_CONTENT}', to: 'datbeo12c@gmail.com'
        }
        failure {
            emailext body: 'failure ${DEFAULT_SUBJECT}', subject: '${DEFAULT_CONTENT}', to: 'datbeo12c@gmail.com'
        }
        changed {
            emailext body: 'change ${DEFAULT_SUBJECT}', subject: '${DEFAULT_CONTENT}', to: 'datbeo12c@gmail.com'
        }
    }

}

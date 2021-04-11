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
                    sh 'docker build -t datsys96/nodejs1104github .'
               }
          }
     }

}

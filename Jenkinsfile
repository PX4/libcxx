pipeline {
  agent none
  stages {
  
    stage('Build') {

      parallel {

        stage('lit') {
          agent {
            docker { image 'px4io/px4-dev-nuttx:2018-11-22' }
          }
          steps {
            sh 'export'
            sh 'ls'
          }
          post {
            always {
              sh 'make distclean'
            }
          }
        }

        stage('test') {
          agent {
            docker { image 'px4io/px4-dev-nuttx:2018-11-22' }
          }
          steps {
            sh 'export'
            sh 'ls'
          }
          post {
            always {
              sh 'make distclean'
            }
          }
        }

      } // parallel
    } // stage: Build

  } // stages

  environment {
    CCACHE_DIR = '/tmp/ccache'
    CI = true
  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '5', artifactDaysToKeepStr: '30'))
    timeout(time: 60, unit: 'MINUTES')
  }
}

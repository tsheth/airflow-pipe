pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        sh 'echo "checkout"'
      }
    }

    stage('DAG build') {
      parallel {
        stage('johndoe whl build') {
          steps {
            sh 'echo "johndoe whl build"'
          }
        }

        stage('speedy whl') {
          steps {
            sh 'echo "build speedy system whl"'
          }
        }

      }
    }

  }
}
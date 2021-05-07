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
        stage('johndoe whl') {
          steps {
            sh 'echo "johndoe whl build"'
          }
        }

        stage('speedy whl') {
          steps {
            sh 'echo "build speedy system whl"'
          }
        }

        stage('filedelta whl') {
          steps {
            sh 'echo "build filedelta whl"'
          }
        }

      }
    }

    stage('push to nexus') {
      steps {
        sh 'echo "push whl to pypi repo"'
      }
    }

    stage('Build airflow image') {
      steps {
        sh 'echo "build airflow image"'
      }
    }

    stage('Approval') {
      parallel {
        stage('Approval') {
          steps {
            input 'Proceed for deployment in kubernetes?'
          }
        }

        stage('github commit / issue') {
          steps {
            sh 'echo "github issue or comment for image build process"'
          }
        }

        stage('Docker image scan') {
          steps {
            sh 'echo "scan docker image for security vulnerability"'
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        sh 'echo "deploy airflow image to kubernetes"'
      }
    }

  }
}
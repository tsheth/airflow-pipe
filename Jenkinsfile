pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        sh 'echo "checkout"'
      }
    }

    stage('Prepare Airflow') {
      parallel {
        stage('Scan docker image') {
          steps {
            sh '''echo "Scan airflow image for vulnerability"
sleep 3'''
          }
        }

        stage('Create Test NS') {
          steps {
            sh '''echo "Creating test namespace"
sleep 4'''
          }
        }

      }
    }

    stage('K8S PVC') {
      steps {
        sh '''echo "Attach PVC to test namespace"
sleep 5
'''
      }
    }

    stage('Deploy Airflow') {
      steps {
        sh '''echo "deploy airflow with K8S commands"
sleep 6'''
      }
    }

    stage('Test Automation') {
      parallel {
        stage('Execute test case') {
          steps {
            sh '''echo "github issue or comment for image build process"
sleep 4'''
          }
        }

        stage('github issue on test case') {
          steps {
            sh '''echo "scan docker image for security vulnerability"
sleep 5'''
          }
        }

      }
    }

    stage('Manual testing') {
      steps {
        input 'Manual testing'
      }
    }

    stage('Destroy Test NS') {
      steps {
        sh '''echo "Destroy test namespace"
sleep 5'''
      }
    }

  }
}
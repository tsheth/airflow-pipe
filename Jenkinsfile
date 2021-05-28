pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        sh 'echo "checkout"'
      }
    }

    stage('Verify K8S PVC') {
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

  }
}
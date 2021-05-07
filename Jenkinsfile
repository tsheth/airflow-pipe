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
            sh '''echo "johndoe whl build"
echo "python3 -m venv venv"
echo "sh \'venv/bin/pip3 install wheel setuptools twine pytest pytest-runner  --proxy=http://dc-proxy-rat.net.vodafone.com:8080\'"
echo "sh \'venv/bin/python3 ./020-development/030-python/130-john_doe/setup.py bdist_wheel\'"
sleep 5
'''
          }
        }

        stage('speedy whl') {
          steps {
            sh '''echo "build speedy system whl"
sleep 3'''
          }
        }

        stage('filedelta whl') {
          steps {
            sh '''echo "build filedelta whl"
sleep 4'''
          }
        }

      }
    }

    stage('push to nexus') {
      steps {
        sh '''echo "push whl to pypi repo"
sleep 3
echo "sh \'venv/bin/python3 -m twine upload --repository-url http://198.18.103.20/mypypi/johndoe/ -u dhirain -p redhat@123 --non-interactive dist/johndoe-0.3.2-py3-none-any.whl\'"'''
      }
    }

    stage('Build airflow image') {
      steps {
        sh '''echo "build airflow image"
sleep 3'''
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
            sh '''echo "github issue or comment for image build process"
sleep 4'''
          }
        }

        stage('Docker image scan') {
          steps {
            sh '''echo "scan docker image for security vulnerability"
sleep 5'''
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        sh '''echo "deploy airflow image to kubernetes"
sleep 5'''
      }
    }

  }
}
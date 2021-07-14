pipeline {
  agent any
  stages {
    stage('JohnDoe Whl') {
      parallel {
        stage('JohnDoe Whl') {
          steps {
            sh 'echo "johndoe whl"'
          }
        }

        stage('Speedy whl') {
          steps {
            sh 'echo "speedy system whl"'
          }
        }

        stage('FileDelta whl') {
          steps {
            sh 'echo "filedelta whl"'
          }
        }

      }
    }

    stage('Docker build and Push') {
      steps {
        sh '''echo "Docker build and push to nexus"
sleep 5
'''
      }
    }

    stage('Docker scanning') {
      steps {
        sh '''echo "docker image scanning"
sleep 6'''
      }
    }

    stage('gitcheckout') {
      steps {
        git(url: 'https://github.com/tsheth/snyk-pipe', branch: 'main', credentialsId: 'git-creds', poll: true, changelog: true)
        sh 'ls -la'
      }
    }

  }
}
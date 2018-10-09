pipeline {
  agent any
    stages {
      stage('One') {
        steps {
          echo 'Hello From Jenkins Trial'
        }
      }

      stage('Two') {
        steps {
          input('Do you want to continue ?')
        }
      }

      stage('Three') {
        when {
          not {
            branch "master"
          }
        }
        steps {
          echo 'Hello Jenkins 2'
        }
      }

      stage('Four') {
        parallel {
          stage('Unit Test') {
            steps {
              echo "Runnint Unit Test.............."
            }
          }
          stage('Integration Test') {
            agent {
              docker {
                image 'ubuntu'
              }
            }
            steps {
              echo "Running Integration Test............."
            }
          }
        }
      }
    }
}

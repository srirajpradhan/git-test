pipeline {
  agent any
    stages {
      stage('One') {
        steps {
          echo 'Hello From Jenkins Trial'
          script {
                env.RELEASE_SCOPE = input message: 'User input required', ok: 'Release!',
                        parameters: [choice(name: 'RELEASE_SCOPE', choices: 'patch\nminor\nmajor\ntrial',
                                     description: 'What is the release scope?')]
            }
            echo "${env.RELEASE_SCOPE}"
       }
      }

      if(env.RELEASE_SCOPE.equals('patch')) {
        stage('Two-A') {
          steps {
            input('Do you want to continue ?')
            }
        }
      } else if(env.RELEASE_SCOPE.equals('minor')) {
        stage('Two-B') {
          steps {
            echo 'Hello Jenkins 2'
          }
        }
      } else if(env.RELEASE_SCOPE.equals('major')) {
        stage("Two-C") {
         steps {
          echo "Helo Two-C"
         }
        }
      }
    }
}

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

      stage('Two') {
        when {
          expression {
            return (env.RELEASE_SCOPE == 'patch')
          }
        }
        steps {
          /* script {
           if(env.RELEASE_SCOPE.equals('patch')) {
              echo 'hello 1'
            } else if (env.RELEASE_SCOPE.equals('minor')) {
              echo 'hello 2'
            } else {
              echo 'hello 3'
            }
          } */
          echo "Patch inside"
          input('Do you want to continue ?')
        }
      }

      stage('Four') {
        when {
          expression {
            return env.RELEASE_SCOPE == 'minor'
          }
        }
        steps {
          echo 'Minor'
          input('Do you want to continue ?')
        }
      }
      stage('Three') {
        steps {
          echo 'Hello Jenkins 2 Regular'
        }
      }
    }
}

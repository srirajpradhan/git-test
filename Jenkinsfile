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
        steps {
          if(env.RELEASE_SCOPE.equals('patch')) {
            input('Do you want to continue ?')
          } else if(env.RELEASE_SCOPE.equals('minor')) {
            echo 'Hello option-2'
          } else {
            echo 'Hello option-any'
          }
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
    }
}

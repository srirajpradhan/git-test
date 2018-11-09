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
    }
}

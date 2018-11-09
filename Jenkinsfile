node {
 stages {
  stage('A') {
    script {
        env.RELEASE_SCOPE = input message: 'User input required', ok: 'Release!',
                parameters: [choice(name: 'RELEASE_SCOPE', choices: 'patch\nminor\nmajor\ntrial',
                             description: 'What is the release scope?')]
    }
    echo "${env.RELEASE_SCOPE}"
  }
  stage('B') {
   if(env.RELEASE_SCOPE.equals('patch')) {
    echo 'Success'
   } else {
    echo 'Success-2'
   }
  }
 }
}

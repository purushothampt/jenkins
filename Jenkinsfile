pipeline{
  agent any

  environment{
    ENV_URL = "pipeline.google.com"
    USER_PWD = credentials("SSH")
  }

  options{
    ansicolor('xterm')
  }

  stages{
    stage ('One'){
      steps{
        addShortText background: '', borderColor: '', color: '', link: '', text: 'ONE'
        sh '''
        echo hello1
        echo hello2
        echo ENVURL = ${ENV_URL}
        '''
      }
    }
    stage ('two'){
      environment{
        ENV_URL = "stage.google.com"
      }
      steps{
        echo "two"
        sh 'echo ENVURL = ${ENV_URL}'
        sh 'env'
        sh '''
        echo -e "//e[31m"
      }
    }
  }
}
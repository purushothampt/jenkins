pipeline{
  agent any

  environment{
    ENV_URL = "pipeline.google.com"
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
      steps{
        echo "two"
        sh 'echo ENVURL = ${ENV_URL}'
      }
    }
  }
}
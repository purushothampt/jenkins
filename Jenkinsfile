pipeline{
  agent any

  environment{
    ENV_URL = "pipeline.google.com"
    USER_PWD = credentials("SSH")
  }

  options{
    ansiColor('xterm')
  }

  triggers{
    pollSCM('*/2 * * * *' )
  }

  tools{
    maven 'maven-3.8.6'
    }

  parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
  }

  stages{
    stage ('One'){
      when {
        environment name: 'CHOICE', value: 'One'
      }
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
      when {
        environment name: 'CHOICE', value: 'One'
      }

      environment{
        ENV_URL = "stage.google.com"
      }
      input {
        message "Should we continue?"
        ok "Yes, we should."
        submitter "alice,bob"
        parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        }
      }
      steps{
        echo "two"
        sh 'echo ENVURL = ${ENV_URL}'
        sh 'env'
        sh '''
        echo -e "//e[31mHello"
        '''
        sh 'mvn --version'
      }
    }
  }
}
pipeline {
    agent any
    environment {
  firstname = "Sonali"
}
parameters {
  booleanParam defaultValue: true, name: 'Do you want to test it?'
  choice choices: ['build', 'test', 'deploy-test', 'deploy-prod'], name: 'task'
  string defaultValue: 'name', name: 'Initiator'
}
    tools{
    maven 'Maven'
    }
   stages {
        stage('Test Stage') {
            steps {
                sh 'ls'
                sh 'echo "The owner of this pipeline is ${firstname}"'
                sh 'echo "The person who initiated this pipeline is ${name}"'
                sh 'echo "The task selected is ${task}"'
                echo 'Hello this is test stage'
                sh 'mvn -e test'
            }
        }
        stage('Build Stage') {
             environment {
  secondname = "Varshney"
}
            steps {
                 echo 'Hello this is build stage'
                 sh 'echo "The person local to build stage is $secondname"'
            }
        }
        stage('Deploy-Test Stage') {
            steps {
                sh 'echo "The person local to build stage is $secondname"'
                echo 'Hello this is deploy test stage'
            }
        }
        stage('Deploy-Prod Stage') {
            steps {
                input 'Do You want to enter into Prod?'
                echo 'Hello this is deploy prod stage'
            }
        }
    }
        post {
  always {
    echo 'This should be print always'
  }
  success {
    echo 'This should be print only if all are successfully build'
  }
  failure {
    echo 'This should be print only if any stage fails'
  }
}
}

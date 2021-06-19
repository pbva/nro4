pipeline {
    agent any

    tools {
        maven 'Maven'
    }
    stages {
      stage ('Initial') {
            steps {
              sh '''
                   echo "PATH = ${PATH}"
                   echo "M2_HOME = ${M2_HOME}"
               '''
            }
        }
        stage("build & SonarQube analysis") {
            agent any
            steps {
              withSonarQubeEnv('sonar') {
                sh 'mvn clean package sonar:sonar'
              }
            }
        }
        stage ('Compilacion') {
            steps {
                 sh 'mvn clean compile -e'
            }
        }
        stage ('Test') {
            steps {
                 sh 'mvn clean test -e'
            }
        }
    }
}

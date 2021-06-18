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
        stage ('Compile') {
            steps {
                 sh 'mvn clean compile -e'
            }
        }
        stage ('Test') {
            steps {
                 sh 'mvn clean test -e'
            }
        }

        stage('SonarQube analysis') {
           steps{
                script {
                        mvn sonar:sonar 
                        -Dsonar.projectKey=Ms-Maven 
                        -Dsonar.host.url=http://localhost:9000 
                        -Dsonar.login=d4da3a7237df0a855aab348de9e21f7b1e16e21b
                        
                                        
                    }
                }
           }
        }
    }
}

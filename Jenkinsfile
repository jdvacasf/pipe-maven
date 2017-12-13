pipeline {
    agent any
    tools { 
        maven 'maven' 
          }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                echo "PATH = ${PATH}"
                echo "M2_HOME = ${M2_HOME}"
                sh 'mvn clean install'
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    post {
        always {
            archive "target/**/*"
            junit 'target/surefire-reports/*.xml'
        }
    }
}

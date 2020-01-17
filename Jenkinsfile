pipeline {
    agent any
    
    tools {
        maven 'M3'
    }
    
    stages {
        
        stage('Checkout') {
            steps {
                echo "-=- Checkout project -=-"
                git url: 'https://github.com/mm167/01_simple_boot.git'
            }
        }
        
        stage('Compile') {
            steps {
                echo "-=- compiling project -=-"
                sh 'mvn clean compile'
            }
            
        }
        stage('Test') {
            steps {
                echo "-=- Test project -=-"
                sh 'mvn test'
            }
            
            post {
                success {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Code coverage') {
            steps {
                jacoco( 
                      execPattern: 'target/*.exec',
                      classPattern: 'target/classes',
                      sourcePattern: 'src/main/java',
                      exclusionPattern: 'src/test*'
                )
            }
        }
    }
}
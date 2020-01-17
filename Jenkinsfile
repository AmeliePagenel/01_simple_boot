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
                sh 'mvn compile'
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
    }
}

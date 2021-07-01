pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Init') {
            steps {
                sh 'pwd'
            }
        }
        stage('Build') {
            steps {
                sh 'pwd && mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
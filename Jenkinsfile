pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /mnt/g/Repository:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
}
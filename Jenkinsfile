pipeline {
    agent any
//     agent {
//         docker {
//             image 'maven:3-alpine'
//             args '-v /root/.m2:/root/.m2'
//         }
//     }
    stages {
        stage('Build') {
            steps {
                batchFile 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                batchFile 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                batchFile './jenkins/scripts/deliver.sh'
            }
        }
    }
}

pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'export PATH=/opt/maven/bin:$PATH && mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'export PATH=/opt/maven/bin:$PATH && mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
            }
        }
        stage('Complete') { 
            steps {
                echo 'Job COmpleted' 
            }
        }
    }
}

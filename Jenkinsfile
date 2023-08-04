pipeline {
    agent {label 'JDK_17'}
    options {
        retry(3)
        timeout(time: 30, unit: 'MINUTES')
    }
    triggers {
        pollSCM('* * * * *')
    }
    tools {
        jdk 'JDK_17'
    }
    stages {
        stage('code') {
            steps {
                git url: 'https://github.com/KVKR31/dummy.git' ,
                branch : 'main'
            }
        }
        stage('package') {
            steps {
                sh 'mvn package'
            }
        }
        stage('build') {
            steps {
<<<<<<< HEAD
                archiveArtifacts artifacts: '**/target/surefire-reports/TEST-*.xml'
                junit testResults : '**/target/surefire-reports/TEST-*.jar'
=======
                archiveArtifacts artifacts: '**/target/surefire-reports/TEST-*.xml',
                junit testResults: '**/target/surefire-reports/TEST-*.xml'
>>>>>>> f531905a03ca63a789b989629593531fb3c7ab7c
            }
        }
    }
    post {
        success {
            mail subject: 'your project is effective',
                 body: 'your project is effective',
                 to: 'vinod@gmail.com'
        }
        failure {
            mail subject: 'your project is failure',
                 body: 'your project is defective',
                 to: 'vinod@gmail.com'
        }
    }
}
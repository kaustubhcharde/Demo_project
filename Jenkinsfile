pipeline {
    agent { label 'node-test' }

    tools {
        maven "M3"
    }

    stages {
        stage('git checkout'){
            steps{
                git 'https://github.com/jglick/simple-maven-project-with-tests.git'
            }     
        }
        stage('Build') {
            steps {
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }

            post {
                success {
                    junit '**/target/surefire-reports/TEST-*.xml'
                    archiveArtifacts 'target/*.jar'
                }
            }
        }
    }
}

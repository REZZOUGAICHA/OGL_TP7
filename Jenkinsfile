pipeline {
    agent any

    stages {

        stage('Test') {
            steps {
                script {
                    bat './gradlew test'
                    archiveArtifacts artifacts: 'build/reports/cucumber/**/*.*', fingerprint: true
                    archiveArtifacts artifacts: 'build/reports/tests/test/**/*.*', fingerprint: true
                }
            }
        }

        stage('Code Analysis') {
            steps {
                withCredentials([string(credentialsId: 'SONAR_AUTH_TOKEN', variable: 'SONAR_AUTH_TOKEN')]) {
                    withSonarQubeEnv('sonarqube') {
                        bat './gradlew sonar'
                    }
                }
            }
        }

        stage('Code Quality') {
            steps {
                timeout(time: 1, unit: 'HOURS') {
                script {
                    def qg = waitForQualityGate()
                    if (qg.status != 'OK') {
                          error "Pipeline aborted due to quality gate failure: ${qg.status}"
                    }
                }
            }
        }

    }}
}


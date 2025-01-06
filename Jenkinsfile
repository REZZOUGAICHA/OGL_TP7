pipeline {
    agent any

    stages {
        stage('Test') {
            steps {
                script {
                    bat './gradlew test'
                    bat './gradlew jacocoTestReport'

                    // Archive test results
                    archiveArtifacts artifacts: 'build/reports/cucumber/**/*.*', fingerprint: true
                    archiveArtifacts artifacts: 'build/reports/tests/test/**/*.*', fingerprint: true

                }
            }
        }

    }
}
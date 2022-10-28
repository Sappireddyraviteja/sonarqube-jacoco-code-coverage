pipeline {
    agent any

    stages {
        stage('Clone sources') {
            steps {
                git branch: 'master', url: 'https://github.com/Sappireddyraviteja/sonarqube-jacoco-code-coverage.gitt'
            }
        }

        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('Qube') {
                    sh "./gradlew sonarqube"
                }
            }
        }
        stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
    }
}

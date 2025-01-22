pipeline {
    agent any

    tools {
        maven 'Maven'
    }

    stages {
        stage("Build") {
            steps {
                sh 'mvn clean package'
            }
        }

        stage("SonarQube") {
            steps {
                script {
                    withSonarQubeEnv('SonarCube') {
                        sh 'mvn sonar:sonar'
                    }
                }
            }
        }

        stage('Clean Up') {
            steps {
                deleteDir()
            }
        }
    }
}

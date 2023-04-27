pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                 git branch: 'main', credentialsId: '2f7e6287-0597-44f3-96ee-7118f14d623c', url: 'https://github.com/amitmaurya0712/jenkins_sonarqube_project.git'
            }
        }
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh 'sonar-scanner \
                        -Dsonar.projectKey=python-project \
                        -Dsonar.projectName=python \
                        -Dsonar.projectVersion=1.0 \
                        -Dsonar.sources=src \
                        -Dsonar.host.url=http://35.92.189.3:9000/ \
                        -Dsonar.login=sqa_7efe3b1b2adb0cc627236ab7f6a57eedd478237f'
                }
            }
        }
    }
}

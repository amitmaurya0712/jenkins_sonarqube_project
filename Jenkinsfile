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
                    sh '/var/lib/jenkins/tools/hudson.plugins.sonar.SonarRunnerInstallation/sonarqube/bin/sonar-scanner \
                        -Dsonar.login=admin \
                        -Dsonar.password=maurya@123 \
                        -Dsonar.projectKey=python-project \
                        -Dsonar.projectName=python-project \
                        -Dsonar.projectBaseDir=/var/lib/jenkins/workspace/ \
                        -Dsonar.projectVersion=1.0 \
                        -Dsonar.sources=.'
                        // -Dsonar.host.url=http://35.92.189.3:9000/ 
                }
            }
        }
    }
}

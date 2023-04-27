pipeline{
    agent any
    tools {

    sonarScanner 'SonarScanner 4.0'
     }
    stages{
        stage("SCM Checkout"){
            steps{
                git branch: 'main', credentialsId: '2f7e6287-0597-44f3-96ee-7118f14d623c', url: 'https://github.com/amitmaurya0712/jenkins_sonarqube_project.git'
            }
        }

        stage("Sonar-Qube"){
            steps{
                    def scannerHome = tool 'sonarqube';
                    withSonarQubeEnv('sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
                        sh "${scannerHome}/bin/sonar-scanner"
                        -D sonar.login=admin \
                        -D sonar.password=admin \
                        -D sonar.projectKey=python \
                        // -D sonar.exclusions=vendor/**,resources/**,**/*.java \
                        -D sonar.host.url="http://35.92.189.3:9000/"
                    }
                }
        }
    }

}
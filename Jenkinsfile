pipeline{
    agent any
    stages{
        stage("SCM Checkout"){
            steps{
                git branch: 'main', credentialsId: '2f7e6287-0597-44f3-96ee-7118f14d623c', url: 'https://github.com/amitmaurya0712/jenkins_sonarqube_project.git'
            }
        }

        stage("Sonar-Qube"){
            steps{
                def scannerHome = tool 'SonarScanner 4.8.0';
                withSonarQubeEnv('sonarqube-server') { 
                sh "${scannerHome}/bin/sonar-scanner"
                }
            }
       }
    }

}
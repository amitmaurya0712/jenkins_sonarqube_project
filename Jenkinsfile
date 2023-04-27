pipeline{
    agent any
    stages{
        stage("SCM Checkout"){
            steps{
                git branch: 'main', credentialsId: '2f7e6287-0597-44f3-96ee-7118f14d623c', url: 'https://github.com/amitmaurya0712/jenkins_sonarqube_project.git'
            }
        }

            stage('Maven Build'){
                steps{
                    def mavenHome = tool name: "Maven-3.8.6", type: "maven"
                    def mavenCMD = "${mavenHome}/bin/mvn"
                    sh "${mavenCMD} clean package"
                }
    }

        stage("Sonar-Qube"){
            steps{
                withSonarQubeEnv('sonarqube-server') {
                sh 'mvn sonar:sonar'
                }
            }
       }
    }

}
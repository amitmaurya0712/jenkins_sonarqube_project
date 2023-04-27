pipeline{
    agent {
        docker {
            image "maven"
        }
    }
    stages{
        // stage('Build'){
        //     steps{
        //         sh 'sudo chmod -R ug+w .'
        //         sh 'mvn clean install -f /var/lib/jenkins/workspace/Sonar_Pipeline/code/pom.xml'
        //     }
        // }

        stage("Sonar-Qube"){
            steps{
                withSonarQubeEnv('sonarqube-server') {
                sh 'mvn sonar:sonar'
                }
            }
       }
    }

}
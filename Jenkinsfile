pipeline{
    agent{
        label "node"
    }
    stages{
        stage("SCM Checkout"){
            steps{
                git branch: 'main', credentialsId: '2f7e6287-0597-44f3-96ee-7118f14d623c', url: 'https://github.com/amitmaurya0712/jenkins_sonarqube_project.git'
            }
        }
    }
}
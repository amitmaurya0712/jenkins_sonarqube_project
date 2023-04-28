pipeline {
    agent any
    parameters {
        choice(name: 'BUILD_TYPE', choices: ['Yes', 'No'], description: 'Select the build type')
        choice(name: 'BUILD_PYTHON', choices: ['Yes', 'No'], description: 'Do you want to build the Python code?')
        choice(name: 'RUN_SONARQUBE', choices: ['Yes', 'No'], description: 'Do you want to run the SonarQube analysis?')
        }
    stages {
        stage('Checkout') {
            steps {
                 git branch: 'main', credentialsId: '2f7e6287-0597-44f3-96ee-7118f14d623c', url: 'https://github.com/amitmaurya0712/jenkins_sonarqube_project.git'
            }
        }

        stage('Build') {
            if (params.BUILD_PYTHON == 'Yes') 
            steps {
                sh "python3 code.py ${params.BUILD_TYPE}"
            }
            else {
                echo "This stage is skipped"
            }


        }

        stage('SonarQube analysis') {
            if (params.RUN_SONARQUBE == 'Yes' )
            steps {
                withSonarQubeEnv('sonarqube_token') {
                    sh '/var/lib/jenkins/tools/hudson.plugins.sonar.SonarRunnerInstallation/sonarqube/bin/sonar-scanner \
                        -Dsonar.login=admin \
                        -Dsonar.password=maurya@123 \
                        -Dsonar.projectKey=python-sonarqube-checkwithparameters \
                        -Dsonar.projectName=python-sonarqube-checkwithparameters  \
                        -Dsonar.projectBaseDir=/var/lib/jenkins/workspace/SonarQube_pipeline \
                        -Dsonar.projectVersion=1.0 \
                        -Dsonar.sources=. '
                        // -Dsonar.host.url=http://35.92.189.3:9000/ 
                }
            }

            else{
                echo "Stage is skipped"
            }
        }
    }
}

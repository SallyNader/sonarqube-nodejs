pipeline {
    agent any
    stages {
        stage("clone") {
            steps {
                git branch: 'main', url: 'https://github.com/SallyNader/sonarqube-nodejs.git'
            }
        }
           stage("sonarqube analysis") {
            steps {
                nodejs(nodeJSInstallationName: 'nodejs') {
                    sh "npm install"
                    withSonarQubeEnv("sonar") {
                        sh """
                            npm set strict-ssl false
                            npm install sonar-scanner
                            npm run sonar
                        """
                    }
                }
            }
        }
    }
}

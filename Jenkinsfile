pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/junedmulla23/Travel_Agency'
            }
        }
        stage('Deploy') {
            steps {
                bat 'xcopy *.html C:\\inetpub\\wwwroot\\ /E /Y'
                bat 'xcopy *.css C:\\inetpub\\wwwroot\\ /E /Y'
            }
        }
        stage('Restart IIS') {
            steps {
                bat 'iisreset'
            }
        }
    }
}

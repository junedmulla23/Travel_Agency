pipeline {
    agent any
   
    environment {
        DEPLOY_DIR = 'C:\\inetpub\\wwwroot\\TravelAgency'
    }
   
    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning project from GitHub...'
                git branch: 'main', url: 'https://github.com/junedmulla23/Travel_Agency.git'
            }
        }
       
        stage('Build') {
            steps {
                echo 'Build Step: Check files in workspace'
                bat 'dir'
            }
        }
       
        stage('Deploy') {
            steps {
                echo 'Deploying all files to IIS folder'
                bat """
                    if not exist "${DEPLOY_DIR}" mkdir "${DEPLOY_DIR}"
                    xcopy /Y /E /I *.* "${DEPLOY_DIR}\\"
                    echo Files deployed successfully
                    dir "${DEPLOY_DIR}"
                """
            }
        }
    }
   
    post {
        success {
            echo 'Pipeline finished successfully! Visit: http://localhost/TravelAgency/index.html'
        }
        failure {
            echo 'Pipeline failed! Check build logs.'
        }
    }
}

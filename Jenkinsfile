pipeline {
    agent {
        label "master"
    }
    environment {
        ORG         = 'jenkinsxio'
        APP_NAME    = 'builder-python'
    }
    stages {
        stage('Docker Deploy') {
            when {
                branch 'master'
            }
            steps {
                echo 'Deploying....'
                sh "docker-compose up --build -d"
            }
        }
    }
}
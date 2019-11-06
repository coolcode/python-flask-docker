pipeline {
    agent {
        label "master"
    }
    environment {
        ORG         = 'jenkinsxio'
        APP_NAME    = 'builder-python'
    }
    stages {
        stage('CI Build and Docker Run') {
            when {
                branch 'master'
            }
            steps {
                container('python') {
                    sh "docker-compose up --build -d"
                }
            }
        }
    }
}
pipeline {
    agent {
        label "jenkins-jx-base"
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
                container('jx-base') {
                    sh "docker-compose up --build -d"
                }
            }
        }
    }
}
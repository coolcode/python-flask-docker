pipeline {
    agent {
        label "master"
        docker { image 'python:3.7.2' }
    }
    environment {
        ORG         = 'blocktest'
        APP_NAME    = 'simple-flask'
    }
    stages {
        stage('Docker Deploy') {
            when {
                branch 'master'
            }
            steps {
                echo 'Deploying....'
                sh "pwd"
                sh "python -V"
                sh "python3 -V"
                sh "pip3 install -r requirements.txt"
                sh "gunicorn --workers 3 -t 30 --graceful-timeout 60 --bind :8000 -m 007 application:app"
                sh "cat gunicorn.log"
            }
        }
    }
}
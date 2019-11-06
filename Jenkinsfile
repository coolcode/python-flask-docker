pipeline {
    agent {
        label "master"
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
                sh "python3 -V"
                withPythonEnv('python3') {
                    sh "python3 -V"
                    sh "pip3 install -r requirements.txt"
                    sh "BUILD_ID=dontKillMe nohup gunicorn --workers 3 -t 30 --graceful-timeout 60 --bind :8000 -m 007 application:app >> gunicorn.log 2>&1 &"
                }
                sh "cat gunicorn.log"
            }
        }
    }
}
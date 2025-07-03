pipeline {
    agent any
    environment {
        VENV_DIR = 'venv'
    }
    stages {
        stage('Prepare Environment') {
            steps {
                sh '''
                    python3 -m venv $VENV_DIR
                    . $VENV_DIR/bin/activate
                    pip install --upgrade pip
                    pip install Django==4.2
                '''
            }
        }
        stage('Start Django Project') {
            steps {
                sh '''
                    . $VENV_DIR/bin/activate
                    django-admin startproject my_django_app .
                    python manage.py migrate
                '''
            }
        }
    }
}

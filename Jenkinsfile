pipeline {
    agent any
    stages {
        stage('Instalar Pylint') {
            steps {
                sh 'pylint --disable=missing-module-docstring hello.py'
            }
        }
        stage('build') { 
            steps {
                sh 'pylint --disable=missing-module-docstring manage.py'
            } 
        }
        stage('deploy') { 
            steps {
                sh 'cp -r ./ /deploy'
            }
        }
    }
}

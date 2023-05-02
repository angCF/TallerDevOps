pipeline {
    agent any
    stages {
        stage('build') { 
            steps {
                sh 'pylint --disable=missing-module-docstring .'
            } 
        }
        stage('deploy') { 
            steps {
                sh 'cp -r ./ /deploy'
            }
        }
    }
}

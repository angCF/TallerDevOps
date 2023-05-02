pipeline {
    agent any
    stages {
        stage('Clonar repositorio') {
            steps {
                git 'https://github.com/usuario/repo.git', branch: 'main'
            }
        }
        stage('build') { 
            steps {
                sh 'pylint --disable=missing-module-docstring ./'
            } 
        }
        stage('deploy') { 
            steps {
                sh 'cp -r ./ /deploy'
            }
        }
    }
}

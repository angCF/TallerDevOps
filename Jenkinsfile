pipeline {
    agent any
    stages {
        /*stage('Clonar repositorio') {
            steps {
                git 'git@github.com:angCF/taller-devops.git', branch: 'main'
            }
        }*/
        stage('build') { 
            steps {
                sh '$WORKSPACE'
                sh 'pylint --disable=missing-module-docstring '
            } 
        }
        stage('deploy') { 
            steps {
                sh 'cp -r ./ /deploy'
            }
        }
    }
}

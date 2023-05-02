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
                sh 'pylint --disable=missing-module-docstring /var/jenkins_home/workspace/app-python'
            } 
        }
        stage('deploy') { 
            steps {
                sh 'cp -r ./ /deploy'
            }
        }
    }
}

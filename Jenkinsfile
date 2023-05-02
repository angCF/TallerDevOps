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
                sh 'pylint --disable=missing-module-docstring /var/jenkins_home/workspace/app-python/blog'
                sh 'pylint --disable=missing-module-docstring /var/jenkins_home/workspace/app-python/personal_portfolio'
                sh 'pylint --disable=missing-module-docstring /var/jenkins_home/workspace/app-python/projects'
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

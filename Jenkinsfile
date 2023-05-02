pipeline {
    agent any
    stages {
        /*stage('Clonar repositorio') {
            steps {
                git 'git@github.com:angCF/taller-devops.git', branch: 'main'
            }
        }*/
        stage('clone repository') {
            steps {
                git branch: "main",
                    url: 'git@github.com:angCF/taller-devops.git'
            }
        }
        stage('build') { 
            steps {
                sh 'find . -name \\*.py | xargs pylint --load-plugins=pylint_django -f parseable | tee pylint.log'
                recordIssues(
                    tool: pyLint(pattern: 'pylint.log'),
                    failTotalHigh: 10
                )
            } 
        }
        stage('deploy') { 
            steps {
                sh 'cp -r ./ /deploy'
            }
        }
    }
}

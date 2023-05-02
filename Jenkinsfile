pipeline {
    agent any
    stages {
        stage('clone repository') {
            steps {
                git branch: "main",
                    url: 'git@github.com:angCF/taller-devops.git'
            }
        }
        stage('build') { 
            steps {
                sh 'find . -path "./venv" -prune -o -name \\*.py | xargs pylint --ignore=venv --exit-zero -f parseable | tee pylint.log'
                recordIssues(
                    tool: pyLint(pattern: 'pylint.log'),
                    failedTotalHigh: 10
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

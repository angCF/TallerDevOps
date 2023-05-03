pipeline {
    agent any
    stages {
        stage('pylit') { 
            steps {
                sh 'find . -path "./venv" -prune -o -name \\*.py | xargs pylint --ignore=venv --load-plugins=pylint_django --exit-zero -f parseable | tee pylint.log'
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

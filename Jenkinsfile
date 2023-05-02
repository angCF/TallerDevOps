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
        state('build') {
            steps {
                sh 'source venv/bin/activate'
                sh 'python3 manage.py runserser'
            }
        }
        stage('deploy') { 
            steps {
                sh 'cp -r ./ /deploy'
            }
        }
    }
}

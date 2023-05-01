pipeline {
    agent any
    stages {
        stage('hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Static Code Checking') {
            steps {
                script {
                    sh 'find . -name \\*.py | xargs pylint --load-plugins=pylint_django -f parseable | tee pylint.log'
                    recordIssues(
                        tool: pyLint(pattern: 'pylint.log'),
                        failTotalHigh: 10,
                    )
                }
            }
        }
        stage('deploy') {
            steps {
                sh 'python manage.py migrate'
                sh 'cp . /deploy' 
                sh 'python3 manage.py runserver /deploy'
            }
        }
    }
}

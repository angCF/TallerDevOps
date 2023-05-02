pipeline {
    agent any 
    stages {
        stage('build') { 
            steps {
                sh 'apt-get update'
                sh 'apt-get upgrade'
                sh 'apt-get install pylint-django'
                sh 'pylint --disable=W1202 --output-format=parseable --reports=no module > pylint.log || echo "pylint exited with $?"'
                sh 'cat render/pylint.log'
            }
        }
        stage('deploy') { 
            steps {
                sh 'cp . /deploy' 
                // sh 'python manage.py migrate'
                sh 'source venv/bin/activate' 
                sh 'python3 manage.py runserver' 
            }
        }
    }
}

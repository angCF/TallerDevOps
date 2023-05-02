pipeline {
    agent any 
    stages {
        stage('build') { 
            steps {
                sh 'sudo apt-get install pylint' 
                sh 'pylint *.py' 
            }
        }
        stage('deploy') { 
            steps {
                sh 'cp . /deploy' 
                sh 'python manage.py migrate'
                sh 'source venv/bin/activate' 
                sh 'python3 manage.py runserver' 
            }
        }
    }
}

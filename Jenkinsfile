pipeline {
    agent any
    stages {
        stage('Instalar Pylint') {
            steps {
                sh 'pylint hello.py'
            }
        }
        stage('build') { 
            steps {
                sh 'pylint --disable=W1202 --output-format=parseable --reports=no module > pylint.log || echo "pylint exited with $?"'
                /*sh 'cat render/pylint.log'*/
            } 
        }
        stage('deploy') { 
            steps {
                sh 'cp -r ../taller-devops /deploy' 
                // sh 'source venv/bin/activate' 
                // sh 'python3 manage.py runserver' 
            }
        }
    }
}

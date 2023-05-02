pipeline {
    agent any 
    stages {
        stage('build') { 
            /* steps {
                sh 'pylint --disable=W1202 --output-format=parseable --reports=no module > pylint.log || echo "pylint exited with $?"'
                sh 'cat render/pylint.log'
            }*/ 
            steps {
                sh """
                    echo ${SHELL}
                    [ -d venv ] && rm -rf venv
                    #virtualenv --python=python2.7 venv
                    virtualenv venv
                    #. venv/bin/activate
                 
                    pip install --upgrade pip
                    pip install -r requirements.txt
                    make clean
                """
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

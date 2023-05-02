pipeline {
    agent any
    stages {
        /* stage('Instalar Pip') {
            steps {
                sh 'apt-get update && apt-get install -y python3-pip'
            }
        }
        stage('Instalar Pylint') {
            steps {
                sh 'pip install pylint'
            }
        }*/
        stage('build') { 
            steps {
                sh 'pylint --disable=W1202 --output-format=parseable --reports=no module > pylint.log || echo "pylint exited with $?"'
                sh 'cat render/pylint.log'
            } 
            /* steps {
                sh """
                    if [ ! -d venv ] ; then
                       virtualenv --python=python2.7 venv
                    fi
                    echo "PWD: ${PWD}"
                    source venv/bin/activate

                    // export PYTHONPATH="$PWD:$PYTHONPATH"

                    pip install pylint
                """
            }*/ 
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

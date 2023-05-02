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
                    if [ ! -d venv ] ; then
                        virtualenv --python=python2.7 venv
                    fi
                        source venv/bin/activate
                       

                        pip install pylint

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

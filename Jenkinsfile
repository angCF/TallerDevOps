opipeline {
    agent any
    stages {
        stage('Instalar Pylint') {
            steps {
                sh 'pylint --version'
            }
        }
        stage('build') { 
            steps {
                sh 'pylint --disable=W1202 --output-format=parseable --reports=no module > pylint.log || echo "pylint exited with $?"'
                /*sh 'cat render/pylint.log'*/
            } 
            /*steps {
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
                sh 'cp -r ./ /deploy' 
                // sh 'python manage.py migrate'
                sh 'source venv/bin/activate' 
                sh 'python3 manage.py runserver' 
            }
        }
    }
}

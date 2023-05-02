pipeline {
    agent any
    stages {
        stage('Instalar Pylint') {
            steps {
                sh 'pylint --disable=missing-module-docstring hello.py'
            }
        }
        stage('build') { 
            steps {
                sh 'pylint --disable=missing-module-docstring > pylint.log || echo "pylint exited with $?"'
                sh 'cat render/pylint.log'
            } 
        }
        stage('deploy') { 
            steps {
                sh 'cp -r ./ /deploy'
            }
        }
    }
}

pipeline {
    agent any
    stages {
        stage('ci/cd pipeline') {
            steps {
                echo "this if from master branch"
            }
        }
        stage('Build developer') {
            when {
                branch 'developer'
            }
            steps {
                  echo "conditional expression applied for developer"
            }
        }
    }
}

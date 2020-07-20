pipeline {
    agent any
    stages {
        stage('ci/cd pipeline') {
            steps {
                echo "this if from master branch"
            }
        }
        stage('Build feature') {
            when {
                branch 'feature'
            }
            steps {
                  echo "conditional expression applied for developer"
            }
        }
    }
}

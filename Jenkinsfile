pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests compile'
            }
        }

        stage('Continuous Testing') {
            steps {
                bat 'mvn -B test'
            }
        }
    }

    post {
        always {
            junit 'target/surefire-reports/*.xml'
        }

        success {
            echo 'All tests passed successfully!'
        }

        failure {
            echo 'Build or testing failed. Check the console output.'
        }
    }
}
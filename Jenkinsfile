pipeline {
    agent any
    stages {
        stage('Build Stage') {
            steps {
                echo "We are at Building is in process..."
           
                echo "Building finished!"
            }
        }
        stage('Testing Stage') {
            steps {
                echo "Testing..."
                echo "Testing finished!"
            }
        }
        stage('Deployment Stage') {
            steps {
                echo "Deploying..."
                echo "Deploying finished"
            }
        }
        
    }
    post {
        always {
            bat "jfrog rt c artifactory-demo --url=http://192.168.33.10:8081/artifactory --user=admin --password=password"
            bat "jfrog rt u  text.txt newfile"
            echo 'We came to an end!'
        }
        success {
            echo 'Build is Successful brother!'
        }
        failure {
            echo 'Sorry mate! Build is Failed! :('
        }
        unstable {
            echo 'Run was marked as unstable'
        }
        changed {
            echo 'Hey look at this, Pipeline state is changed.'
        }
    }
}

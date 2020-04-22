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
            powershell 'jfrog rt c my_server --url=http://localhost:8081/artifactory --user=admin --password=password'
            powershell 'jfrog rt u text.txt newfile/build_version_$(get-date -f MM-dd-yyyy)_$(get-date -f HH:mm:ss)/'
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

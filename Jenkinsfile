pipeline {
    agent any
    
    tools {
        maven 'maven'
    }
    
    stages {
        stage('Pull the source code from GitHub') {
            steps {
                echo 'Automatically triggered by webhook'
               git branch: 'main', url: 'https://github.com/allwinrajan/web-application-deployment-to-nginx.git'
            }
        }

        stage('push to nginx web server') {
            steps {
                script {
                    def containerName = 'webapp'
                    def containerPath = '/usr/share/nginx/html'
                    
                    sh """
                        docker cp ./index.html ${containerName}:${containerPath}/index.html
                    """
                }
            }
        }
    }
    
    post {
        success {
            echo 'Build success'
        }
        failure {
            echo 'Build failure'
        }
    }
}

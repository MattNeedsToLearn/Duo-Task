pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    sh '''
                    docker build -t mattneedstolearn/duo-task:latest .
                    docker build -t mattneedstolearn/duo-nginx:latest ./nginx
                    '''
                }
            }
        }
        stage('Push') {
            steps {
                script {
                        sh '''
                        docker push mattneedstolearn/duo-task:latest
                        docker push mattneedstolearn/duo-nginx:latest
                        '''
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                        sh '''
                        kubectl apply -f ./k8s -n dev
                        kubectl rollout restart flask-deployment  --namespace=dev
                        kubectl rollout restart nginx-deployment  --namespace=dev
                        '''
                }
            }
        }
        stage('Clean Up') { 
            steps {
                sh '''
                echo "nothing here yet"
                '''
            }
        }
    }
}


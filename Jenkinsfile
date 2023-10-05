pipeline {
    agent any
    stages {
        stage('Appease the Machine Spirit - Build') {
            steps {
                script {
                    sh '''
                    docker build -t mattneedstolearn/duo-task:latest .
                    docker build -t mattneedstolearn/duo-nginx:latest ./nginx
                    '''
                }
            }
        }
        stage('Recite the Centicle of Communication - Push') {
            steps {
                script {
                    sh '''
                    docker push mattneedstolearn/duo-task:latest
                    docker push mattneedstolearn/duo-nginx:latest
                    '''
                }
            }
        }
        stage('Empower the Machine Spirit - Deploy') {
            steps {
                script {
                        sh '''
                        kubectl apply -f ./k8s -n dev
                        kubectl rollout restart deployment flask-deployment  --namespace=dev
                        kubectl rollout restart deployment nginx-deployment  --namespace=dev
                        '''
                }
            }
        }
        stage('Apply Sacred Unguents - Clean Up') { 
            steps {
                sh '''
                echo "nothing here yet"
                '''
            }
        }
    }
}


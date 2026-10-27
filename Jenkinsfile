pipeline {
    agent any

    stages {
        stage('Check Kubernetes') {
            steps {
                sh '''
                    kubectl version --client
                    kubectl config current-context
                '''
            }
        }

        stage('Deploy Application') {
            steps {
                sh '''
                    kubectl apply -f k8s/deployment.yaml
                    kubectl apply -f k8s/service.yaml
                '''
            }
        }

        stage('Verify Deployment') {
            steps {
                sh '''
                    kubectl get deployments
                    kubectl get pods
                    kubectl get services
                '''
            }
        }
    }
}

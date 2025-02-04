pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[clusterName: 'EKS-1',credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://85C4188D504382EB391EA1A1D665785D.gr7.us-east-1.eks.amazonaws.com']]) {
                    
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[clusterName: 'EKS-1',credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://85C4188D504382EB391EA1A1D665785D.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

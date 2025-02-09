pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[clusterName: 'EKS-1',credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://FC09849BAE670398AA0F620649F5DA90.gr7.us-east-1.eks.amazonaws.com']]) {
                    
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[clusterName: 'EKS-1',credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://FC09849BAE670398AA0F620649F5DA90.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

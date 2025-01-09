pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-5', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B366CEDBE2315E879710CD3A3F7E3DB1.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-5', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B366CEDBE2315E879710CD3A3F7E3DB1.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

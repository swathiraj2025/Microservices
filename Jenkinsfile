pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[clusterName: 'EKS-2',credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6BCA884394A3721F63303D8DF5A4F772.yl4.us-east-1.eks.amazonaws.com']]) {
                    sh 'kubectl config view'
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[clusterName: 'EKS-2',credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6BCA884394A3721F63303D8DF5A4F772.yl4.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

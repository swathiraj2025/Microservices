pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[clusterName: 'EKS-12',credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://C43D0A2DCE47A78BBA4B911473FC9484.sk1.us-west-1.eks.amazonaws.com']]) {
                    
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[clusterName: 'EKS-12',credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://C43D0A2DCE47A78BBA4B911473FC9484.sk1.us-west-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

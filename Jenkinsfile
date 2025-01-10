pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-new', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://0D041A20B90BB5AC90CBA93BCCC3DDF1.sk1.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-new', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://0D041A20B90BB5AC90CBA93BCCC3DDF1.sk1.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

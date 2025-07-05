pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-Ramkrishna1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://39E5CBFF88B8A9E33B9A51525A2CA004.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-Ramkrishna1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://39E5CBFF88B8A9E33B9A51525A2CA004.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

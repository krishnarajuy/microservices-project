pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-krishna1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://06EE90084D5EB8F609D431CA16E07A64.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-krishna1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://06EE90084D5EB8F609D431CA16E07A64.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

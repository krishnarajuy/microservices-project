pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-krishna1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://9A57C5ED5DD40078C1268EA26D659AD4.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-krishna1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://9A57C5ED5DD40078C1268EA26D659AD4.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-anji', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://F2DC2982CD620AD20B13889958E9E323.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-anji', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://F2DC2982CD620AD20B13889958E9E323.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

pipeline {
    agent any
    

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'dev-medium-eks-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://EF31EA20B2EB978C0AEE4E42F222CC87.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'dev-medium-eks-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://EF31EA20B2EB978C0AEE4E42F222CC87.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

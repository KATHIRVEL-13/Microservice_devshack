pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
              withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-3', contextName: '', credentialsId: 'k8-token', namespace: 'wenapps', serverUrl: 'https://11A2A5EB7E02385F0A66F59E3A9F9C9A.gr7.ap-south-1.eks.amazonaws.com']]) {
                   sh "kubectl apply -f deployment-service.yml"
                   sleep 60
                }
            }
        }
        
         stage('Verify deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-3', contextName: '', credentialsId: 'k8-token', namespace: 'wenapps', serverUrl: 'https://11A2A5EB7E02385F0A66F59E3A9F9C9A.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}

pipeline {
    agent any

    stages {
        stage('Deploy to kuberenetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'devopsshack-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://51FE07CB65DC3D08F1EB5F8DDF300502.gr7.ap-south-1.eks.amazonaws.com']]) {
                     sh "kubectl apply -f deployment-service.yml"
                     
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'devopsshack-cluster', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://51FE07CB65DC3D08F1EB5F8DDF300502.gr7.ap-south-1.eks.amazonaws.com']]) {
                     sh "kubectl get svc -n webapps"
                     
                }
            }
        }
    }
}

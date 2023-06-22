pipeline {
    agent any
    stages {
        stage('---Deployment---') { 
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'Server-Credentials', keyFileVariable: 'KEY', usernameVariable: 'USERNAME')]) {
                    sh '''ssh -i $KEY -o StrictHostKeyChecking=accept-new -T $USERNAME@40.114.114.65 <<EOF
                    DIR="/home/azureuser/Website-Template"
                    pwd
                    cd "$DIR"
                    pwd
                    exit
                    EOF'''
                }
            }
        }
    }
}

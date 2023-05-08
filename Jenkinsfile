pipeline {
    agent any
    stages {
        stage('---Deployment---') { 
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'Server-Credentials', keyFileVariable: 'KEY', usernameVariable: 'USERNAME')]) {
                    sh '''ssh -i $KEY -o StrictHostKeyChecking=accept-new -T $USERNAME@52.188.67.140 <<EOF
                    cd /home/azureuser/Website-Template
                    git pull origin master
                    sudo cp -r * /var/www/html/
                    exit
                    EOF'''
                }
            }
        }
    }
}

pipeline {
    agent any

    stages {
        stage('---Deployment---') { 
            environment {
                SERVER_CREDS = credentials('Server-Credentials')
            }
            steps {
                sh '''ssh -i $SERVER_CREDS -o StrictHostKeyChecking=accept-new -T $SERVER_CREDS_USR@52.188.67.140 <<EOF
                cd /home/azureuser/Website-Template
                git pull origin master
                sudo cp -r * /var/www/html/
                exit
                EOF'''
            }
        }
    }
}

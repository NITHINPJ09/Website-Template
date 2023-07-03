pipeline {
    agent any
    stages {
        stage('---Deployment---') { 
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'Server-Credentials', keyFileVariable: 'KEY', usernameVariable: 'USERNAME')]) {
                    sh '''ssh -i $KEY -o StrictHostKeyChecking=accept-new -T $USERNAME@52.136.117.106 <<EOF
                    if [ -d "/home/azureuser/Website-Template" ]
                    then 
                        cd /home/azureuser/Website-Template
                        git pull origin master
                        sudo cp -r * /var/www/html/
                    else 
                        git clone https://github.com/NITHINPJ09/Website-Template.git
                        cd /home/azureuser/Website-Template
                        sudo cp -r * /var/www/html/
                    fi
                    exit
                    EOF'''
                }
            }
        }
    }
}

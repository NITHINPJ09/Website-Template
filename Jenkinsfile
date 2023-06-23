pipeline {
    agent any
    stages {
        stage('---Deployment---') { 
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: 'Server-Credentials', keyFileVariable: 'KEY', usernameVariable: 'USERNAME')]) {
                    sh '''ssh -i $KEY -o StrictHostKeyChecking=accept-new -T $USERNAME@20.25.70.147 <<EOF
                    DIR="/home/azureuser/Website-Template"
                    word="first"
                    echo "$DIR"
                    echo "\$DIR"
                    echo "test"
                    echo "first word = $word"
                    echo "second word = \$word"
                    if [ -d "\$DIR" ]
                    then 
                        cd "\$DIR"
                        git pull origin master
                        sudo cp -r * /var/www/html/
                    else 
                        git clone https://github.com/NITHINPJ09/Website-Template.git
                        cd "\$DIR"
                        sudo cp -r * /var/www/html/
                    fi
                    exit
                    EOF'''
                }
            }
        }
    }
}

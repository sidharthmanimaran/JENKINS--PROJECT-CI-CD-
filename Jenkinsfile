pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/sidharthmanimaran/JENKINS--PROJECT-CI-CD-.git'
            }
        }

        stage('Deploy Website') {
            steps {
                sh '''
                scp -i /var/lib/jenkins/keypair.pem \
                -o StrictHostKeyChecking=no \
                -r * \
                ubuntu@52.66.88.116:/home/ubuntu/deploy/

                ssh -i /var/lib/jenkins/keypair.pem \
                -o StrictHostKeyChecking=no \
                ubuntu@52.66.88.116 "
                sudo rm -rf /var/www/html/*
                sudo cp -r /home/ubuntu/deploy/* /var/www/html/
                sudo systemctl reload nginx
                "
                '''
            }
        }

    }
}

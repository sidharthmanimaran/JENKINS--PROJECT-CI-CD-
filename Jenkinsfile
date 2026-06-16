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
                ssh -i /var/lib/jenkins/keypair.pem \
                -o StrictHostKeyChecking=no \
                ubuntu@52.66.88.116 "mkdir -p /tmp/website"

                scp -i /var/lib/jenkins/keypair.pem \
                -o StrictHostKeyChecking=no \
                -r * \
                ubuntu@52.66.88.116:/tmp/website/

                ssh -i /var/lib/jenkins/keypair.pem \
                -o StrictHostKeyChecking=no \
                ubuntu@52.66.88.116 "
                sudo cp -r /tmp/website/* /var/www/html/
                sudo systemctl reload nginx
                "
                '''
            }
        }

    }
}

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
                ubuntu@3.109.155.163 "mkdir -p /tmp/website"

                scp -i /var/lib/jenkins/keypair.pem \
                -o StrictHostKeyChecking=no \
                -r * ubuntu@3.109.155.163:/tmp/website/
                '''
            }
        }
    }
}

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
                scp -i /home/ubuntu/keypair.pem -o StrictHostKeyChecking=no \
                -r * ubuntu@3.109.155.163:/tmp/website
                '''
            }
        }
    }
}

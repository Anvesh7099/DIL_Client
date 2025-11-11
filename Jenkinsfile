pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Anvesh7099/DIL_Client.git'
            }
        }

        stage('Build') {
            steps {
                dir('node-hello-world') {
                    sh 'npm install'
                }
            }
        }

        stage('Run Locally') {
            steps {
                dir('node-hello-world') {
                    sh '''
                    echo "🟢 Stopping any running app..."
                    pm2 delete node-hello-world || true

                    echo "🚀 Starting Node.js app locally..."
                    sudo npm install -g pm2 || true
                    pm2 start server.js --name node-hello-world
                    pm2 save

                    echo "✅ App deployed and running locally on port 3000!"
                    '''
                }
            }
        }
    }
}


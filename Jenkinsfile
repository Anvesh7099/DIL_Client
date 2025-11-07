pipeline {
  agent any

  stages {
    stage('Checkout Code') {
      steps {
        git branch: 'main', url: 'https://github.com/Anvesh7099/DIL_Client.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Build App') {
      steps {
        sh 'npm run build || echo "No build script found"'
      }
    }

    stage('Deploy') {
      steps {
        sh '''
        sudo rm -rf /var/www/html/*
        sudo cp -r build/* /var/www/html/
        echo "✅ Deployed build files to /var/www/html/"
        '''
      }
    }
  }
}


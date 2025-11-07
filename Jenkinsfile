pipeline {
  agent any

  stages {
    stage('Checkout Code') {
      steps {
        git branch: 'main', url: 'https://github.com/Anvesh7099/DIL_Client.git'
      }
    }

    stage('Deploy to NGINX') {
      steps {
        sh '''
        echo "🧹 Cleaning old files..."
        sudo rm -rf /var/www/html/*

        echo "📦 Copying new files to NGINX root..."
        sudo cp -r * /var/www/html/

        echo "✅ Deployment successful! Visit: http://3.85.208.233"
        '''
      }
    }
  }
}


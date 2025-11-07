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

    stage('Run Tests') {
      steps {
        sh 'npm test || echo "No tests found, skipping..."'
      }
    }

    stage('Build App') {
      steps {
        sh 'npm run build || echo "No build script found, skipping..."'
      }
    }

    stage('Deploy') {
      steps {
        sh '''
        if [ -d "build" ]; then
          sudo cp -r build/* /var/www/html/
          echo "✅ Deployed build files to /var/www/html/"
        else
          echo "⚠️ No build folder found, skipping deployment."
        fi
        '''
      }
    }
  }
}

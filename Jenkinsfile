pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', url: 'https://github.com/spring-projects/spring-petclinic.git'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package -DskipTests'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test || echo "⚠️ Tests failed but continuing in DEV"'
      }
    }

    stage('Archive Artifact') {
      steps {
        archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
      }
    }

    stage('Deploy') {
      steps {
        sh '''
        echo "🚀 Deploying to DEV server..."
        sudo cp target/*.jar /var/www/html/
        echo "✅ Deployment complete!"
        '''
      }
    }
  }
}


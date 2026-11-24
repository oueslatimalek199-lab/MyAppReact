pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps { checkout scm }
    }

    stage('Build') {
      steps {
        sh 'docker build -t mern-server ./Server'
        sh 'docker build -t mern-client ./Client'
      }
    }

    stage('Deploy & Test') {
      steps {
        sh 'docker compose up -d --build'
        sh 'sleep 15'
        sh 'docker compose exec -T server wget -qO- http://localhost:9000/api/health'
        sh 'docker compose exec -T client wget -qO- http://localhost:3000'
      }
    }
  }

  post {
    always { sh 'docker compose down || true' }
    success { echo 'Pipeline OK' }
    failure { echo 'Pipeline en échec' }
  }
}
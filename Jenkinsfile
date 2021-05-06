pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    stage('Install Bundler') {
      steps {
        sh "gem install bundler "
      }
    }
    stage('Build') {
      steps {
        echo 'Building ...'
        sh """
        bundle install
        """
      }
    }
    stage('Test') {
      steps {
        echo 'Testing ...'
        sh "bundle exec rake"
      }
    }
  }
  post {
    always {
      archive "reports/test-results/**/*"
      junit "reports/test-results/*.xml"
    }
  }
}

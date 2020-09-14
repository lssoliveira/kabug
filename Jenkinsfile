pipeline {
    agent {
        docker {
            image 'qaninja/rubywd'
        }
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building or Resolve Dependencies!'
                sh 'bundle install'
            }
        }
        stage('Test') {
            steps {
                echo 'Running Regression Tests'
                sh 'bundle exec cucumber -p ci'
            }
        }
        stage('UAT') {
            steps {
                echo 'Wating for User Acceptance'
                input(message: 'Go yo production?', ok: 'Yes')
            }
        }
        stage('Prod') {
            steps {
                echo 'WebApp is Ready :)'
            }
        }
    }
}
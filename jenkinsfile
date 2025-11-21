pipeline {
    agent any

    environment {
        COMPOSE_DIR = "/opt/dev-wordpress"   // where Jenkins will deploy
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/YOURUSER/YOURREPO.git'
            }
        }

        stage('Deploy Dev WordPress') {
            steps {
                sh '''
                mkdir -p $COMPOSE_DIR
                cp -r * $COMPOSE_DIR/
                cd $COMPOSE_DIR

                docker-compose down
                docker-compose pull
                docker-compose up -d --build
                '''
            }
        }
    }
}

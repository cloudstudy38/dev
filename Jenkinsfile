pipeline {
    agent any

    environment {
        COMPOSE_DIR = "/opt/dev-wordpress"   // where Jenkins will deploy
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/cloudstudy38/dev.git', credentialsId: 'github-pat'
            }
        }

        stage('Deploy Dev WordPress') {
            steps {
                sh '''
                    mkdir -p $COMPOSE_DIR
                    cp -r * $COMPOSE_DIR/
                    cd $COMPOSE_DIR

                    /usr/local/bin/docker-compose down
                    /usr/local/bin/docker-compose pull
                    /usr/local/bin/docker-compose up -d --build
                '''

            }
        }
    }
}

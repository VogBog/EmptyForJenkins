pipeline {
    agent any
    stages {
        stage ("Build") {
            steps {
                echo "Сборка приложения..."
            }
        }
        stage ("Test") {
            steps {
                echo "Тестирование приложения..."
            }
        }
        stage ("Deploy to Staging") {
            steps {
                echo "Развёртывание приложения в staging..."
                sh ".deploy staging"
            }
        }
        stage ("Deploy to Production") {
            steps {
                echo "Развёртывание приложения в прод..."
                sh "./deploy production"
            }
        }
    }
    post {
        failure {
            echo "Задача провалена"
            mail to: "vogbog92@gmail.com",
                 subject: "${env.JOB_NAME} - Сборка №${env.BUILD_NUMBER} провалилась",
                 body: "Для более подробной информации откройте Jenkins ${env.BUILD_URL}"
        }
    }
}

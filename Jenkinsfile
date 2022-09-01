pipeline {
    agent any

    stages {
        stage('GITHUB clone') {
            steps {
                echo 'Cloning from github'
                git 'https://github.com/wakaleo/game-of-life.git'
            }
        }
        stage('artifactor build stage') {
            steps {
                echo 'build with maven'
                sh 'mvn clean install'
            }
        }
        stage('deploy with war') {
            steps {
                echo 'deploy woth tomcat'
                deploy adapters: [tomcat9(credentialsId: '07a25f33-b07c-4e02-ae1a-17e668dbb215', path: '', url: 'http://54.163.71.251:8080/')], contextPath: null, onFailure: false, war: '**/*.war'
            }
        }
    }
}

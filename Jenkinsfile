pipeline {
    agent any
    tools {
        maven "M3"
    }
    environment {
    registryfront = "whiteteam/react-front"
        registryCredentials = "dockerhub_id"
        dockerImageFront = ""
    registryback = "whiteteam/spring-back"
        dockerImageBack = ""
    }
    stages {
        stage('Checkout Git Repositories') {
            steps {
                // Checkout first Git repository
                dir('frontEnd') {
                    git(
                        url: 'https://github.com/jrhuc/lbg-car-react-starter.git',
                        branch: 'main'
                    )
                }

                 
                // Checkout second Git repository
                dir('backEnd') {
                    git(
                        url: 'https://github.com/jrhuc/lbg-car-spring-app-starter.git',
                        branch: 'main'
                    )
                }
            }
        }
        stage('Test Spring build') {
            steps {
                dir('backEnd') {
                    sh "ls" 
                    script {
                       docker.build(registryback) 
                    }
                }
            }
        }
        stage('Test React build') {
            steps {
                dir('frontEnd') {
                    sh "ls" 
                    script {
                       docker.build(registryfront) 
                    }
                }
            }
        }
    }
}

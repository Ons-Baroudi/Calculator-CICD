pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Code source récupéré depuis GitHub'
            }
        }

        stage('Build calc-service') {
            steps {
                dir('calc-service') {
                    sh 'docker build -t 192.168.20.134:5000/calculator-calc:2.0 .'
                }
            }
        }

        stage('Build sum-service') {
            steps {
                dir('sum-service') {
                    sh 'docker build -t 192.168.20.134:5000/calculator-sum:2.0 .'
                }
            }
        }

        stage('Build sub-service') {
            steps {
                dir('sub-service') {
                    sh 'docker build -t 192.168.20.134:5000/calculator-sub:2.0 .'
                }
            }
        }

        stage('Build mul-service') {
            steps {
                dir('mul-service') {
                    sh 'docker build -t 192.168.20.134:5000/calculator-mul:2.0 .'
                }
            }
        }

        stage('Build div-service') {
            steps {
                dir('div-service') {
                    sh 'docker build -t 192.168.20.134:5000/calculator-div:2.0 .'
                }
            }
        }
        stage('Push images') {
        steps {
            sh 'docker push 192.168.20.134:5000/calculator-calc:2.0'
            sh 'docker push 192.168.20.134:5000/calculator-sum:2.0'
            sh 'docker push 192.168.20.134:5000/calculator-div:2.0'
            sh 'docker push 192.168.20.134:5000/calculator-mul:2.0'
            sh 'docker push 192.168.20.134:5000/calculator-sub:2.0'
        }
    }
    }

    post {
        success {
            echo 'CI : toutes les images ont été construites avec succès !'
        }
        failure {
            echo 'CI : échec du pipeline.'
        }
    }
}

pipeline{
    tools{ 
        jdk 'java 8 openjdk'
        maven 'maven'
    }
    agent none //set to none if multiple agents will be used
    stages{
        stage('Checkout'){
            agent any
            steps{
                git 'https://github.com/manuelrodgzz/game-of-life'
            }
        }
        stage('Compile'){
            agent any
            steps{
                sh 'mvn compile'
            }
        }
        stage('Test'){
            agent any
            steps{
                sh 'mvn test'
            }
            post{
                //create user friendly reports
                always{
                    junit 'gameoflife-web/target/surefire-reports/*.xml'
                }
            }
        }
        stage('Package'){
            agent {label 'win_slave'}
            steps{
                git 'https://github.com/manuelrodgzz/game-of-life'
                bat 'mvn package' //windows uses bat, not sh
            }
        }
    }
}

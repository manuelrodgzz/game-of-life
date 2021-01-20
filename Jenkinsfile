pipeline{
    tools{ 
        jdk 'java 8 openjdk'
        maven 'maven'
    }
    agent none
    stages{
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
                always{
                    junit 'gameoflife-web/target/surefire-reports/*.xml'
                }
            }
        }
        stage('Package'){
            agent {label: 'win_slave'}
            steps{
                git 'https://github.com/manuelrodgzz/game-of-life'
                bat 'mvn package'
            }
        }
    }
}

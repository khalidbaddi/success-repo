pipeline {

    agent any 

    stages{

        stage('GIT CHECKOUT'){

            steps{
                git branch: 'main', url: 'https://github.com/khalidbaddi/success-repo.git'
            }
        }
        stage('UNIT TESTING'){

            steps{
                sh 'mvn test'
            }
        }
        stage('INTEGRATION TESTING'){

            steps{
                sh 'mvn verify -DskipUnitTests'
            }
        }
        stage('MAVEN BUILD'){

            steps{
                sh 'mvn clean install'
            }
        }
        stage('STATIC CODE ANALYSIS'){

            steps{
                script{
                   withSonarQubeEnv(credentialsId: 'sonar') {
                    sh 'mvn clean package sonar:sonar'   
                }  
              }
            }
        }
        stage('QUALITY GATE STATUS'){
            steps{
                script{
                    waitForQualityGate abortPipeline: false, credentialsId: 'sonar'

                }
            }
        }
    }
}

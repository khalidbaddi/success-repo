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
    }
}

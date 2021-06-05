pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/hemanth22/HCL_Test.git'
            }
        }

        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn -B test' 
            }
        }
        stage('Sonar Test') { 
            steps {
                withEnv(['SONAR_TOKEN=token']) {
                    sh 'mvn verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar' 
                }
            }
        }
    }
}

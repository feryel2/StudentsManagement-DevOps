pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }

    stages {
        stage('GIT') {
            steps {
                git branch: 'main', url: 'https://github.com/feryel2/StudentsManagement-DevOps.git'
            }
        }

        stage('Compile Stage') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage('MVN SONARQUBE') {
    steps {
        withCredentials([string(credentialsId: 'sonar-token', variable: 'SONAR_TOKEN')]) {
            withSonarQubeEnv('SonarQube') {
                sh '''
                mvn clean verify sonar:sonar \
                -Dsonar.projectKey=student-management \
                -Dsonar.login=$SONAR_TOKEN
                '''
            }
        }
    }
}

    }
}


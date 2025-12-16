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
       withCredentials([string(credentialsId: 'squ_a49efc71d0c25e76d19d43d8c332d3348e3b6134', variable: 'SONAR_TOKEN')]) {
                    sh 'mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=$SONAR_TOKEN' 
        }
    }
}

    }
}


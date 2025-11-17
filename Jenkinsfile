pipeline {
    agent any
    stages {
        stage("Git Clone") {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[credentialsId: 'GIT_HUB_CREDENTIALS', url: 'https://github.com/DDouraid/Aawen_Devops.git']]])
            }
        }
        stage('Nettoyage du projet') {
            steps {
                sh 'mvn clean'
            }
        }
        stage('MVN Package') {
            steps {
                sh "mvn package -DskipTests=true"
            }
        }
        stage('SONARQUBE') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.login=e9085ee87c56742400195eb9b4268923f7143138'
            }
        }

    }
    post {
        success {
            emailext (
                subject: 'Construction réussie',
                body: 'La construction du projet a réussi. Tout est en ordre!',
                to: 'drididouraiid@gmail.com'
            )
        }
        failure {
            emailext (
                subject: 'Construction échouée',
                body: 'La construction du projet a échoué. Veuillez vérifier les logs.',
                to: 'drididouraiid@gmail.com'
            )
        }
    }
}


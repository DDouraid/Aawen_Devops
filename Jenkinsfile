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
        stage('MVN SONARQUBE') {
            steps {
                sh 'mvn sonar:sonar'
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


pipeline {
    agent any
    
    stages {
    
        stage('build') {
            steps {
                sh "./mvnw package"
            }
        }
    
        stage("capture") {
            steps {
                archiveArtifacts '**/target/*.jar'
                jacoco()
                junit '**/target/surefire-reports/TEST*.xml'
            }
        }
    }
    
    post {
        always {
            echo "Notify failed build jobs by email from here!."
        }
    }
    
}  

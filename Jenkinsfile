pipeline {
    agent any
    
    stages {
        
        stage("checkout") {
            steps {
                git branch: 'main', url: 'https://github.com/adamgali/course3-jenkins-gs-spring-petclinic.git'
            }
        }
    
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

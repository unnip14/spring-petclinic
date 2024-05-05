pipeline {
    agent { label 'jdk17' }
    options {
                timeout(time: 1, unit: 'HOURS')
                 retry(3)

    }

    stages {
        stage('source-code and sonarcube') {
            steps {
                git url: 'https://github.com/unnip14/spring-petclinic.git', branch: 'main'            }
        }
    


       stage('code-build') {
            steps {
                 withSonarQubeEnv('Sonar_parctice') {
                sh script : '/opt/apache-maven-3.9.6/bin/mvn clean package sonar:sonar'         
            }
          }
        }
    stage('reporting') {
            steps {
                junit testResults: 'target/surefire-reports/*.xml'      }
        }


}
post { 
        success { 
            echo 'success done!'
        }
    }

}

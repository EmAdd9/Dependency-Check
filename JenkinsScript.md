
Please replace the placeholders with your actual credentials and values before executing the pipeline. The sensitive information has been replaced with placeholders (`**`) in this Markdown representation.


```groovy
pipeline {
    agent any
    
    tools{
        jdk 'jdk11'
        maven 'maven3'
    }
    environment {
        SCANNER_HOME=tool 'sonar-scanner'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'repository_url'
            }
        }
        stage('Mvn Compile') {
            steps {
                sh "mvn clean compile"
            }
        }
        stage("Test Cases"){
            steps{
                sh "mvn test"
            }
        }
        
        stage("Sonarqube Analysis"){
            steps{
                withSonarQubeEnv('sonar-server') {
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=project_name \
                    -Dsonar.java.binaries=. \
                    -Dsonar.projectKey=project_name '''
    
                }
            }
        }
        stage("Build"){
            steps{
                sh "mvn clean package"
            }
        }
        stage('OWASP Dependency Check') {
            steps {
                dependencyCheck additionalArguments: '--scan target/', odcInstallation: 'owasp'
                     dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }
        stage("Deploy to TomCat"){
            steps{
                sh "sudo cp target/*.war /opt/apache-tomcat-9.0.65/webapps/"
            }
        }

    }
}

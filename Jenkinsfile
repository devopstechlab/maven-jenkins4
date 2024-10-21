pipeline {
    agent any
    tools{
        maven 'Maven3'
        jdk 'java17'
    }
    stages {
        stage('Download-code GIT') {
            steps {
                echo "Download code from GIT"
                git branch: 'main', url: 'https://github.com/KajalLad1206/maven-jenkins4.git'
            }
        }
        stage('Build') {
            steps {
                 echo "Build Java project maven"
                 sh 'mvn clean package'
            }
        }
        stage('Archive-Artifact') {
            steps {
                echo "Archiving the artifact"
                archiveArtifacts artifacts: '**/*.war', followSymlinks: false
            }
        }
        stage('Build-Deploy-Job-Trigger') {
            steps {
                echo "Trigering deploy job automatically"
                build wait: false, job: 'pipeline-deploy'
            }
        }
        
    }
}

pipeline {

    agent any

    stages {
    
        stage('Download new Version') {
        
            steps {
            
                sh 'wget -P /opt/Jenkins/seleniumHub/ $VersionDownloadURL'
            
            }        
        
        }
        
        stage('Remove currect version') {
        
            sh 'echo "removing current version"'
        
        }        
        
        stage('Deploy new version') {
        
            sh 'echo "Deployinf new version"'
        
        }
        
        stage('Test') {
        
            sh 'echo "testing new version"'
        
        }
    
    
    }


}

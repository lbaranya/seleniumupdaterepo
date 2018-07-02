pipeline {

    agent any

    stages {
    
        stage('Download new Version') {
        
            steps {
            
                sh 'wget -P /opt/Jenkins/seleniumHub/ $VersionDownloadURL'
            
            }        
        
        }
        
        stage('Remove currect version') {
            steps {
        
                sh 'echo "removing current version"'
            }
        }        
        
        stage('Deploy new version') {
        
            steps  {
                sh 'echo "Deployinf new version"'
            }
        }
        
        stage('Test') {
        
            steps {
                sh 'echo "testing new version"'
            }
        
        }
    
    
    }


}

pipeline {
    agent any 
    
    triggers 
    { 
        githubPush() 
    
    }
    
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
                sh 'ls -lh ./target'
            }

        }
        
         stage('S3 artifact upload') {
            steps {
                sh 'ls -lh'
                sh 'aws s3 cp $WORKSPACE/target s3://hello-world-amex-gbt --recursive --include "*"'
            }

        }
   }
   
}

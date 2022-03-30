pipeline {
    agent any 
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
               
                sh 'aws s3 cp ./target/original-jb-hello-world-maven-0.2.0.jar s3://hello-world-amex-gbt/ --recursive'
            }

        }
   }
   
}

pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello from GitHub hook trigger'
            }
        }
        stage('Build') {
            steps {
                echo 'Building'
            }
        }    
        stage('Deploy') {
            steps {
                echo 'Deploying'
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'MyAWS',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                        sh(script: 'aws s3 cp /var/lib/jenkins/workspace/JenkinsPipeline/index.html https://ap-northeast-1.console.aws.amazon.com/s3/buckets/test-env-jenkins-01?region=ap-northeast-1&bucketType=general&tab=objects')
                }
            }
        }
         stage('Test') {
            steps {
                echo 'Testing'
            }
         }        
        stage('Release') {
            steps {
                echo 'Releaseing'
            }    
        }
    }
}

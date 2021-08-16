pipeline {
    agent any
    environment {
        PROJECT_ID = 'virtual-anchor-319409'
    }
    stages {

        stage('Example') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }

        stage ('Build') {
            steps {
                sh '''
                    docker version 
                    docker build -t helloworld:$BUILD_NUMBER .
                '''
            }            
        }

        stage ('Tgging & Pushing the image'){
            steps{
                sh '''

                    docker tag helloworld:$BUILD_NUMBER gcr.io/$PROJECT_ID/helloworld:$BUILD_NUMBER
                    docker push gcr.io/$PROJECT_ID/helloworld:$BUILD_NUMBER
                '''
            }
        }

        stage ('Test') {
            steps {
                echo 'Testing .........'
                sh 'kubectl'
            }
        }

        stage ('Deploy'){
            steps{
                echo 'Deploying ..........'
            }
        }

    }
}
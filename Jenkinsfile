pipeline{

    agent any

    stages{


        stage('git checkout'){

            steps{

                git branch: 'master',
                url: 'https://github.com/gavademahesh98/log-in-vel.git'
            }
        }

        stage('Build'){

            steps{

            sh  'docker build -t maheshg98/mylogin:${BUILD_NUMBER} .'
                    
             }
        }
        stage('push-image'){
            steps{

            sh """
                  docker login -u maheshg98 -p Mahesh@8798
                  docker push maheshg98/mylogin:${BUILD_NUMBER}
            """
            }
        }
        stage('deployment'){

            steps{
                sh """
                    docker pull maheshg98/mylogin:${BUILD_NUMBER}
                    docker run -itd -p 4545:8080 --name login-app-${BUILD_NUMBER} maheshg98/mylogin:${BUILD_NUMBER}

                """
            }
        }






    }
}
pipeline {
    agent any

    environment {
        VENV = 'venv'
        MY_CRED = credentials('docker_credentials')
    }

    stages {
        stage ("Install") {
            steps {
                sh '''
                    python3 -m venv $VENV
                    . $VENV/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }
        stage ("Linting") {
            steps {
                script {
                    echo "This is my Linting Step"
                }
            }
        }
        stage ("Install Packages") {
            steps {
                script {
                    echo "This is Install PAkcges Step"
                }
            }
        }
        stage("Docker Build and Push") {
            steps {
                script {
                    echo "Building and pushing Docker image"
                    withCredentials([usernamePassword(credentialsId: 'docker_credentials', 
                                                  usernameVariable: 'USERNAME', 
                                                  passwordVariable: 'PASSWORD')]){

                        sh '''
                            docker login -u $USERNAME -p $PASSWORD
                            docker build -t dock .
                            docker tag dock midhileshp/jenkins-docker
                            docker push midhileshp/jenkins-docker
                        '''
                        }
                    }
                }
            }
        stage ("Run Application") {
            steps {
                script {
                    echo "This is my Run applcaition Step"
                }
            }
        }

    }
}

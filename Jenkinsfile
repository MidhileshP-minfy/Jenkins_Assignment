pipeline {
    agent any

    environment {
        VENV = 'venv'
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

                    sh '''
                        docker login -u midhileshp -p Y@mini!23
                        docker build -t dock .
                        docker tag dock midhileshp/jenkins-docker
                        docker push midhileshp/jenkins-docker
                    '''
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

pipeline {
    agent any
    stages {
        stage('Install Dependencies') {
            steps {
                sh 'pip install scikit-learn'
            }
        }
        stage('Run Script') {
            steps {
                sh 'python3 model.py'
            }
        }
        stage('Build Image') {
            steps {
                sh '''
                    docker build -t ml_img .
                    docker run -d --name mcon -p 2000:5000 ml_img
                '''
            }
        }
    }
}

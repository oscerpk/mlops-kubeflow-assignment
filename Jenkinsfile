pipeline {

    agent any

    stages {

        stage('Environment Setup') {
            steps {
                echo "Setting up environment..."
                sh """
                python3 -m venv jenv
                . jenv/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                """
            }
        }

        stage('Pipeline Validation') {
            steps {
                echo "Running MLflow pipeline script..."
                sh """
                . jenv/bin/activate
                python run_pipeline.py
                """
            }
        }

    }

    post {
        always {
            echo "Pipeline Finished!"
        }
        success {
            echo "SUCCESS!"
        }
        failure {
            echo "FAILED!"
        }
    }
}

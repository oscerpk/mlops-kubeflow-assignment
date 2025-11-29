pipeline {
    agent any

    environment {
        PYTHON_VERSION = "3.10"
    }

    stages {

        stage('Environment Setup') {
            steps {
                echo "=== Stage 1: Checkout + Python Setup ==="

                // Checkout code
                checkout scm

                // Create virtual environment
                sh """
                    python3 -m venv venv
                    source venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                """
            }
        }

        stage('Pipeline Compilation') {
            steps {
                echo "=== Stage 2: Compile Kubeflow Pipeline ==="

                sh """
                    source venv/bin/activate
                    python pipeline.py
                """

                // Fail if pipeline.yaml not generated
                sh """
                    if [ ! -f pipeline.yaml ]; then
                        echo "pipeline.yaml NOT FOUND!"
                        exit 1
                    fi
                """
            }
        }

        stage('Run ML Pipeline') {
            steps {
                echo "=== Stage 3: Execute MLflow Pipeline ==="

                sh """
                    source venv/bin/activate
                    python run_pipeline.py
                """
            }
        }
    }

    post {
        always {
            echo "Cleaning workspace..."
            deleteDir()
        }
        success {
            echo "Pipeline SUCCESS ✓"
        }
        failure {
            echo "Pipeline FAILED ✗"
        }
    }
}

pipeline {
    agent { 
        node {
            label 'docker-agent-python'
        }
    }
    triggers {
        // This will poll SCM for changes every minute
        pollSCM('* * * * *')  
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                cd myapp
                python3 -m venv venv  # Create a virtual environment
                . venv/bin/activate     # Activate the virtual environment
                pip install -r requirements.txt  # Install requirements
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                . venv/bin/activate   # Activate the virtual environment
                python3 hello.py
                python3 hello.py --name=Test
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}

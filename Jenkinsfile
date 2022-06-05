pipeline{
    agent{label 'python_new'}
    stages{
        stage('source code'){
            steps{
                git 'https://github.com/vishnuprabhu01/python-sample-vscode-flask-tutorial.git'
            }
        }
        stage ('install dependencies'){
            steps{
                sh 'pip install setuptools wheel'
                 }
        }
        stage('Install requirements'){
            steps{
              sh  'pip install -r requirements.txt'
            }
        }
        stage('Test Results'){
            steps{
                sh 'pip install pytest'
                sh '/home/jenkins/.local/bin/pytest --doctest-modules --junitxml=junit/test-results.xml --cov=. --cov-report=xml'
                }
        }
        stage('SonarQube analysis') {
            steps{
                withSonarQubeEnv('SONAR_MAIN ') {
                   sh '/home/ubuntu/root_workspace/workspace/python_free/sonar-scanner-4.7.0.2747-linux/bin/sonar-scanner \
                                                -Dsonar.projectKey=my_python-1 \
												-Dsonar.sources=. \
												-Dsonar.host.url=http://54.149.133.244:9000 \
												-Dsonar.login=8a1699b9d4e828e4a49de0e5b70da0451d0aaef6'
                                                  }
                 }
            }
       }
    }
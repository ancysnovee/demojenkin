pipeline{
    agent any
    stages{
        stage('clone repo'){
            steps{
                git  credentialsId: 'Demoproject' , url:"https://github.com/ancysnovee/demojenkin.git",branch:"main"
            }
            
        }
        stage('Dependency'){
            steps{
                echo 'installing dependencies'
                bat '''
                    python -m venv venv
                    call venv\\Scripts\\activate
                    pip install --upgrade pip
                    pip install pytest
                    '''
            }
        }
        stage ('test'){
            steps{
                echo 'running tests'
                bat '''
                    call venv\\Scripts\\activate
                    pytest test.py
                    '''
                    
            }
        }
        stage ('deploy'){
            steps{
                echo 'deploying application'
                bat '''
                    call venv\\Scripts\\activate
                    python stack.py
                    '''
            }
        }
    }
    post{
        success{
            echo "pipeline success"
        }
        failure{
            echo "pipeline failure"
        }
    }
    
}



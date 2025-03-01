pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // This checks out the code from the repository.
                sh 'git clone https://github.com/shaharm192/MySoftware.git'

            }
        }
        stage('Run Script') {
            steps {
                script {
                    // Jenkins sets BRANCH_NAME for multibranch pipelines.
                    if (env.BRANCH_NAME == 'main') {
                        // For the master branch, simply run the script.
                        echo "Running welcom.py on main branch..."
                        sh 'python welcom.py'
                    } else if (env.BRANCH_NAME?.startsWith("NewButton")) {
                        echo "Running Click.py on a NewButton branch..."
                        sh 'python Click.py'
                        error("Intentional failure for NewButton branch")
                    } else {
                        echo "Branch ${env.BRANCH_NAME} does not trigger any specific action."
                    }
                }
            }
        }
    }
}

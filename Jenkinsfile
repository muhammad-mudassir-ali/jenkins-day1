pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Cloning repository from GitHub...'
                checkout scm
            }
        }

        stage('Validate Files') {
            steps {
                echo 'Validating project files...'
                bat 'dir'
            }
        }

        stage('Build') {
            steps {
                echo 'Building AutoElite Motors website...'
                echo 'Static website — no build step required'
            }
        }

        stage('Test') {
            steps {
                echo 'Running basic tests...'
                bat '''
                    IF EXIST index.html (
                        echo PASS: index.html exists
                    ) ELSE (
                        echo FAIL: index.html missing
                        exit /b 1
                    )

                    IF EXIST style.css (
                        echo PASS: style.css exists
                    ) ELSE (
                        echo FAIL: style.css missing
                        exit /b 1
                    )

                    IF EXIST Jenkinsfile (
                        echo PASS: Jenkinsfile exists
                    ) ELSE (
                        echo FAIL: Jenkinsfile missing
                        exit /b 1
                    )

                    echo All tests passed!
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying AutoElite Motors website...'
                bat '''
                    IF NOT EXIST "C:\\autoelite-deploy" mkdir "C:\\autoelite-deploy"
                    copy index.html "C:\\autoelite-deploy\\index.html"
                    copy style.css  "C:\\autoelite-deploy\\style.css"
                    echo Files deployed successfully!
                    dir "C:\\autoelite-deploy"
                '''
            }
        }

    }

    post {
        success {
            echo 'Pipeline completed successfully! AutoElite website is live.'
        }
        failure {
            echo 'Pipeline failed. Check the logs above for details.'
        }
        always {
            echo 'Pipeline finished.'
        }
    }
}

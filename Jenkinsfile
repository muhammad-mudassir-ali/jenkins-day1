pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo '📥 Cloning repository from GitHub...'
                checkout scm
            }
        }

        stage('Validate HTML') {
            steps {
                echo '🔍 Validating HTML files...'
                sh 'ls -la'
                sh 'test -f index.html && echo "✅ index.html found" || echo "❌ index.html missing"'
                sh 'test -f style.css && echo "✅ style.css found" || echo "❌ style.css missing"'
            }
        }

        stage('Build') {
            steps {
                echo '🏗️ Building AutoElite Motors website...'
                echo '✅ Static website — no build step required'
                sh 'echo "Build completed at: $(date)"'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running basic tests...'
                sh '''
                    echo "--- Checking required files ---"
                    test -f index.html && echo "PASS: index.html exists" || (echo "FAIL: index.html missing" && exit 1)
                    test -f style.css  && echo "PASS: style.css exists"  || (echo "FAIL: style.css missing"  && exit 1)
                    test -f Jenkinsfile && echo "PASS: Jenkinsfile exists" || (echo "FAIL: Jenkinsfile missing" && exit 1)

                    echo "--- Checking HTML content ---"
                    grep -q "AutoElite" index.html && echo "PASS: Brand name found in HTML" || (echo "FAIL: Brand name missing" && exit 1)
                    grep -q "style.css" index.html  && echo "PASS: CSS linked in HTML"       || (echo "FAIL: CSS not linked"      && exit 1)

                    echo "--- All tests passed! ✅ ---"
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Deploying AutoElite Motors website...'
                echo '📁 Copying files to web server directory...'
                sh '''
                    mkdir -p /tmp/autoelite-deploy
                    cp index.html /tmp/autoelite-deploy/
                    cp style.css  /tmp/autoelite-deploy/
                    echo "✅ Files deployed to /tmp/autoelite-deploy"
                    ls -la /tmp/autoelite-deploy/
                '''
            }
        }

    }

    post {
        success {
            echo '🎉 Pipeline completed successfully! AutoElite website is live.'
        }
        failure {
            echo '❌ Pipeline failed. Check the logs above for details.'
        }
        always {
            echo '🏁 Pipeline finished. Stage: ${currentBuild.currentResult}'
        }
    }
}

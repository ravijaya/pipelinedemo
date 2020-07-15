node('master') {
    stage("Fetch Source Code") {
		cleanWs()
        git([url: 'https://github.com/ravijaya/pipelinedemo', branch: 'add_functions_and_tests']) 
    }
    
    dir('.') {
        printMessage('Running Pipeline')
        stage("Testing") {
			sh ls -la
            sh 'python test_functions.py'
        }
        stage("Deployment") {
            if (env.BRANCH_NAME == 'master') {
                printMessage('Deploying the master branch')
            } else {
                printMessage("No deployment for branch [${env.BRANCH_NAME}]")
            }
            
        }
        printMessage('Pipeline Complete')
    }
}

def printMessage(message) {
    echo "${message}"
}

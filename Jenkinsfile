#! groovy


pipeline {
    agent {
    }
    environment {
        BUILD_VERSION = nextVersionFromGit(scope)
    }
    stages {
        stage('Install'){
            steps {
                echo "Installing ..."
            }
        }
        stage('Test'){
            steps {
                echo "Testing ..."
            }
        }
        stage('Deploying'){
            steps {
                echo "Deploying ..."
            }
        }
    }
}

// Pull existing latest tags and increments by 1 tags for latest commint and pushes to git.
// Uses same tag for build release

def nextVersionFromGit(scope){
    def latestVersion = sh returnStdout: true, script: 'git describe --tags "$(git rev-list --tags=*.*.* --max-count=1 2> /dev/null)" 2> /dev/null || echo 0.0.0'
    def(major, minor, patch) = latestVersion.tokenize('.').collect { it.toInteger() }
    latestVersion
}
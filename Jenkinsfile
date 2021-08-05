pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'echo $GIT_COMMIT'
                def r = sh script: 'echo $GIT_PREVIOUS_SUCCESSFUL_COMMIT', returnStatus: true
                echo "Previous commit ID:  {$r} "
                sh "git diff --name-only --oneline $GIT_PREVIOUS_SUCCESSFUL_COMMIT $GIT_COMMIT > result2.txt"
                sh '/var/jenkins_home/corona_wrap/bin/embold-ci-cd-wrapper -c $WORKSPACE/repository-configuration.json -lf result2.txt'
            }
        }
    }
}

node {
    def root = tool name: 'Go1.8', type: 'go'
    ws("${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_ID}/src/github.com/neeraj-2/golang-ci-jenkins-pipeline") {
        withEnv(["GOROOT=${root}", "GOPATH=${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_ID}/", "PATH+GO=${root}/bin"]) {
            env.PATH="${GOPATH}/bin:$PATH"
            
            stage 'Checkout'
        
            git url: 'https://github.com/neeraj-2/golang-ci-jenkins-pipeline.git'
        
            stage 'preTest'
            bat 'go version'
            
            stage 'Test'
            bat 'go vet'
            bat 'go test -cover'
            
            stage 'Build'
            bat 'go build .'
            
            stage 'Deploy'
            // Do nothing.
        }
    }
}

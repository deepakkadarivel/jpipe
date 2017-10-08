#!/usr/bin/env groovy

node {
    // Install the desired Go version
    def root = tool name: 'Go 1.8', type: 'go'

    // Export environment variables pointing to the directory where Go was installed
    withEnv(["GOROOT=${root}", "PATH+GO=${root}/bin"]) {
        shell 'go version'
    }

    // Checkout the code from Github, stages allow Jenkins to visualize the different sections of your build steps in the UI
      stage('Checkout from GitHub') {
        // No special needs here, if your projects relys on submodules the checkout step would need to be different
        checkout scm
      }

      stage("run app") {
        go run main.go
      }
}
#!groovy

pipeline {
agent any

options {
// if you have a powerful server you can enable concurrent builds
disableConcurrentBuilds()
timeout(time: 5, unit: "MINUTES")
}

environment {
NODE_ENV="production"
}

stages {
stage("SETUP") {
agent {
docker {
image "node"
}
}
steps {
script {
sh "npm test"
}
}
}
}
}

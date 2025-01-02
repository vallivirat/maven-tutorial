node {
    // Define the workspace and tools
    def mavenHome = tool name: 'MAVEN_HOME', type: 'maven'
    def javaHome = tool name: 'JAVA_HOME', type: 'jdk'

    // Set environment variables for Maven and Java
    env.PATH = "${mavenHome}/bin:${javaHome}/bin:${env.PATH}"

    stage('Checkout') {
        echo 'Checking out code from repository...'
        checkout scm
    }

    stage('Build') {
        echo 'Running Maven clean and install...'
        sh 'mvn clean install'
    }

    stage('Test') {
        echo 'Running Maven tests...'
        sh 'mvn test'
    }

    stage('Post-Build') {
        echo 'Archiving test reports...'
        junit '**/target/surefire-reports/*.xml' // Archive test reports
    }
}

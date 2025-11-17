node {

    stage('Checkout') {
        echo "Cloning project from GitHub..."
        checkout scm
    }

    stage('Build') {
        echo "Running Maven Build..."
        bat 'mvn clean install'
        // Use 'sh' if your Jenkins agent is Linux:
        // sh 'mvn clean install'
    }

    stage('Test') {
        echo "Executing test cases..."
        bat 'mvn test'
    }

    stage('Package') {
        echo "Packaging WAR file..."
        bat 'mvn package'
    }

    stage('Archive WAR') {
        echo "Archiving WAR to Jenkins Artifacts..."
        archiveArtifacts artifacts: 'target/*.war', fingerprint: true
    }
}

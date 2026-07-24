pipeline {
    agent none

    stages {
        stage('Back-end') {
            agent {
                docker { image 'maven:3.8.1-adoptopenjdk-11' }
            }
            steps {
                echo "--- Running Java / Maven Hello World ---"
                
                // Write a temporary Java file and execute it using single-file execution in Java 11
                sh '''
                    cat << 'EOF' > HelloWorld.java
                    public class HelloWorld {
                        public static void main(String[] args) {
                            System.out.println("Hello World from Java 11 inside Maven container!");
                        }
                    }
EOF
                    java HelloWorld.java
                '''
            }
        }

        stage('Front-end') {
            agent {
                docker { image 'node:16-alpine' }
            }
            steps {
                echo "--- Running Node.js Hello World ---"
                
                // Execute an inline JavaScript script using Node
                sh '''
                    node -e 'console.log("Hello World from Node.js inside Alpine container!");'
                '''
            }
        }
    }
}

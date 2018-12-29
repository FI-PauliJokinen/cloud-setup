// This shows a simple build wrapper example, using the AnsiColor plugin.
pipeline {
    agent any
    environment { 
                AWS_ACCESS_KEY== credentials('aws-access-key') 
                AWS_SECRET_KEY== credentials('aws-secret-key') 
    }
    parameters {
        string(defaultValue: "TEST", description: 'What environment?', name: 'userFlag')
        choice(choices: ['US-EAST-1', 'US-WEST-2'], description: 'What AWS region?', name: 'region')
    }
    stages {
    // This displays colors using the 'xterm' ansi color map.
        stage ("1. packer test") {
          steps {
            sh "echo 'aws_access_key=${environment.AWS_ACCESS_KEY}' 
            sh "chmod packer/jenkins/packer.sh 755; packer/jenkins/packer.sh \
              -var 'aws_access_key=${environment.AWS_ACCESS_KEY}' \
              -var 'aws_secret_key=${environment.AWS_SECRET_KEY}' \
              d.json "
            }
        } 
    }
}


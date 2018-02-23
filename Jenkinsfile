#!/usr/bin/env groovy

pipeline {
    
    agent  any
    
   /* stages {
        
        
        
        stage('Build') {
            steps {
                echo 'Building...'
               
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
               
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
               
            }
        }
    }*/
        
    
    
    stages {
        stage ('push artifact') {
            steps {
                sh 'mkdir archive'
                sh 'echo test > archive/test.txt'
                zip zipFile: 'test.zip', archive: false, dir: 'archive'
                archiveArtifacts artifacts: 'test.zip', fingerprint: true
            }
        }

        stage('pull artifact') {
            steps {
                step([  $class: 'CopyArtifact',
                        filter: 'test.zip',
                        fingerprintArtifacts: true,
                        projectName: 'Sample1',
                        selector: [$class: 'SpecificBuildSelector', buildNumber: '${BUILD_NUMBER}']
                ])
                unzip zipFile: 'test.zip', dir: './archive_new'
                sh 'cat archive_new/test.txt'
            }
        }
    }
}
    
    
    
    
    
    
}

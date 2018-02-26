#!/usr/bin/env groovy

pipeline {
    
    agent  any
    
   stages {
        
        
        
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
       
       
       
         stages {
     stage('Copy Archive') {
         steps {
             script {
                 step ([$class: 'CopyArtifact',
                 projectName: 'Sample-project',
                 filter: "build/libs/*.jar",
                 target: 'var/www']);
             }
         }
     }
    }
    }
        
    
    
  
   
}

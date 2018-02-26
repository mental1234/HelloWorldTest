pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/mental1234/HelloWorldTest.git', branch: 'master')
        sh '''#! /bin/bash
mvn clean
mvn bash
 '''
      }
    }
  }
}
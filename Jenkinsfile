pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/mental1234/HelloWorldTest.git', branch: 'master')
        sh '''#! /bin/bash
mvn clean
mvn install
pwd
 '''
      }
    }
    stage('VersioningArtifactory') {
      steps {
        sh '''#!/bin/bash
# Credentials
USER="user"
PASS="ramonesparza"
# repo and path
REPO="test"
FILENAME=""

curl -u ${USER}:${PASS} -X PUT ec2-13-59-196-122.us-east-2.compute.amazonaws.com/${REPO}/${FILENAME} -T ${FILENAME}


'''
      }
    }
  }
}
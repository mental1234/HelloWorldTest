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

# Upload file
cd target
FILE=$(ls | grep *.war)

# Credentials
USER="user"
PASS="ramonesparza"

# Repo and directory
URL="ec2-13-59-196-122.us-east-2.compute.amazonaws.com/artifactory"
REPO="test"
FOLDER="HW_Proj"

curl -u ${USER}:${PASS} -X PUT ${URL}/${REPO}/${FOLDER}/${FILE} -T ${FILE}
'''
      }
    }
    stage('DeployArtifact') {
      steps {
        sh '''#! /bin/bash

URL="http://ec2-13-59-196-122.us-east-2.compute.amazonaws.com/artifactory"
USER="user"
PASS="ramonesparza"

cd target
FILE=$(ls | grep *.war)

cd ${WORKSPACE}
mkdir -p Deploy
cd Deploy
curl -u ${USER}:${PASS} ${URL}/test/HW_Proj/${FILE} > HW.war



'''
      }
    }
  }
}
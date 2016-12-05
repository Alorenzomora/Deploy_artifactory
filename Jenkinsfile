#!groovy
import hudson.*
import hudson.model.*
import jenkins.*
import jenkins.model.*
	
node {
  stage ('Create a file'){
  writeFile file: "Deploy_artifactory.txt", test: "Test 05/12/2016"
  
  }
  stage('Deploy_Artifact'){
		//sh 'docker login -u admin -p password docker-virtual.art.local'
		//sh 'docker push docker-virtual.art.local/basic-image-builder'
		
		// Create the upload spec.
		def uploadSpec = """{
				"files": [
						{
							"pattern": "Deploy_artifactory.txt",
							"target":  "test-generic"
						}
					]
				}"""
				
		def buildInfo = Artifactory.newBuildInfo()
		buildInfo.setName "Test/Dockerfile"
		def server = Artifactory.server 'artifactory-bsi'
		server.upload spec: uploadSpec, buildInfo: buildInfo
		server.publishBuildInfo buildInfo
    }
}

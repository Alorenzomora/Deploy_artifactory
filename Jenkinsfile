node {
  stage ('Create a file'){
  writefile: "Deploy_artifactory.txt", Test: "Test 05/12/2016"
  
  }
  stage('Deploy_Artifact'){
		//sh 'docker login -u admin -p password docker-virtual.art.local'
		//sh 'docker push docker-virtual.art.local/basic-image-builder'
		
		// Create the upload spec.
		def uploadSpec = """{
				"files": [
						{
							"pattern": "Dockerfile",
							"target": "dockerfiles/${envs.pipelineName}/"
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

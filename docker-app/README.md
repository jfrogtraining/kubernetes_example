## Create a product Docker image
* Downloads, from Artifactory, the ‘webservice-1.1.2.war’ file and the ‘docker-framework’ Docker
 image, that were created in the previous two pipelines
* Creates a ‘docker-app’ production Docker image
* Pushes it to Artifactory
* Scans it with Xray
* Promotes it to a production repository in Artifactory

### Step to create Jenkins Pipeline:
<b>Note:</b> List of required Jenkins plugins
*   [Artifactory Plugin](https://wiki.jenkins.io/display/JENKINS/Artifactory+Plugin)   
*   [Docker Pipeline Plugin](https://wiki.jenkins.io/display/JENKINS/Docker+Pipeline+Plugin)   
*   [GitHub plugin](https://plugins.jenkins.io/git)   
*   [Pipeline Github Plugin](https://wiki.jenkins.io/display/JENKINS/Pipeline+Github+Plugin)   
*   [Pipeline Plugin](https://wiki.jenkins.io/display/JENKINS/Pipeline+Plugin)   

1.  On the Jenkins front page, click on Credentials -> System -> Global credentials -> Add Credentials
    Add your Artifactory credentials as the type Username with password, with the ID artifactory-credentials 
    ![Add_Artifactory_Credentials](images/Add_Credentials.png)
    
2.  Create new Jenkins Pipeline Job.

3.  Add String Parameters:
    *   ARTDOCKER_REGISTRY (String Parameter) : Domain of Artifactory docker registry 
		e.g `ARTDOCKER_REGISTRY : docker.artifactory`
    *   REPO (String Parameter) -> Artifactory virtual docker registry<Br>
		e.g.  `REPO -> docker`
    *   PROMOTE_REPO (String Parameter) : Artifactory production docker registry<Br>
	    e.g. `PROMOTE_REPO -> docker-prod-local`
    *   SOURCE_REPO (String Parameter) : Artifactory staging docker registry<Br>
    	e.g. `SOURCE_REPO -> docker-stage-local`
    *   SERVER_ID (String Parameter) : Artifactory Server Id<Br>
    	e.g. `SERVER_ID -> artifactory`
    *   XRAY_SCAN (Choice Parameter) : Xray Scan. Applicable only if you are using JFrog Xray<Br>
        e.g. `XRAY_SCAN -> YES`
    *   SERVER_URL (String Parameter) : Artifactory Server URL<Br>
        e.g. `SERVER_URL -> http://35.225.27.231/artifactory`
    *   CREDENTIALS (Credentials Parameter) : Artifactory Credential<Br>
        e.g. `CREDENTIALS -> YES`
    
    	
4.  Copy [Jenkinsfile](Jenkinsfile) to Pipeline Script.

5.  To build it, press Build Now.

6.  Check your newly published build in build browser of Artifactory.

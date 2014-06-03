# Yeoman Configurations


###**Fresh Installation of Yeoman Setup**


	01. Download [node.js](http://nodejs.org/) install and add to path.
	    Go to shell or command prompt to check whether it is installed
	    $ node --version
	      
	02. Download [GIT-Bash](http://git-scm.com/) install and add to path.	
	    Go to shell or command prompt to check wheter it is installed
	    $ git --version 

	03. Configure git to use https. Enter the below command 
        $ git config --global url."https://".insteadOf git://

	04. Download [Ruby](https://www.ruby-lang.org/en/) install  and add to path.

	    Go to shell or command prompt to check whether it is installed
	    $ ruby --version

	05. Install sass and compass.
	    Note : install sass first and strict to the mentioned versions
	    $ gem install sass --version "3.2.10"
	    $ gem install compass --version "0.12.2" 
		
	09. Install yeoman 
	    $ npm install -g yo
	    
	10. Install grunt
	    $ npm install -g grunt-cli
	    
	11. Install bower
	    $ npm install -g bower
	    
	10. Install yeoman-generators using these commands   
	   $ npm install -g generator-webapp
	   $ npm install -g generator-angular



###**Existing installation to setup Yeoman**

	01. Configure git to use https. Enter the below command 
        $ git config --global url."https://".insteadOf git://

	02. Run commands to clean npm and bower
	    $ npm cache clean
	    $ bower cache clean

	03. Run commands to uninstall Compass and sass 
	    $ gem uninstall compass
	    $ gem uninstall sass

	04. Run commands to install sass and compass the following versions
 	   Note : install sass first and strict to the mentioned versions
	    $ gem install sass --version "3.2.10"
	    $ gem install compass --version "0.12.2" 

	05. Install yeoman 
	    $ npm install -g yo
	    
	06. Install grunt
	    $ npm install -g grunt-cli
	    
	07. Install bower
	    $ npm install -g bower
	    
	08. Install yeoman-generators using these commands   
	    $ npm install -g generator-webapp
	    $ npm install -g generator-angular


## To Use Generators

#####Angular Generator
	01. Create a folder, go into it and run command: yo angular.
	02. Run command the following commands to :
	
	    ###### To start grunt server #####
	    $ grunt serve

	    ###### To run grunt build #####
	    $ grunt build
	    
	    ###### To check the dist build #####
	    $ grunt server:dist

## Grunt build using Maven
Step 1. Add this plugin in the ui project pom.xml
	    

	<plugin>    
		 <groupId>com.github.trecloux</groupId>
		 <artifactId>yeoman-maven-plugin</artifactId>
		 <version>0.1</version>
		 <executions>
			<execution>
				<goals>
					<goal>build</goal>
				</goals>
			</execution>
		 </executions>
	   </plugin>
	   <plugin>
		<groupId>org.apache.maven.plugins</groupId>
		<artifactId>maven-war-plugin</artifactId>
		<version>2.4</version>
		<configuration>
			<packagingExcludes>WEB-INF/lib*.jar</packagingExcludes>
			<failOnMissingWebXml>true</failOnMissingWebXml>
			<webResources>
			 <resource>
			   <directory>yo/dist</directory>
			 </resource>
			 <resource>
		       <filtering>true</filtering>
		        <directory>src/main/webapp</directory>
		     </resource>
		    </webResources>
		</configuration>
	</plugin>
		
Step 2. Make sure the ui project should be of below structure :

        project-ui
		|---src
		|
		|---yo
		|    |-----app
		|    |-----node_modules
		|    |-----bower.json
		|    |-----...
		|    |-----...remaining grunt files
		|    |-----...
		|
		|----pom.xml
		
	Note: 'yo' folder should be in the project-ui.

Step 3. In bower.json of yo folder in ui project make sure the file will not have 'dependencies' and 'devDependencies', so which will not load the bower_components at the build time.

        So, Your bower.json file should be like this:
		Before removing the dependencies and devDependencies :
		-------------------------------------------------------
		{
		  "name": "BaseProject",
		  "version": "0.0.0",
		  "dependencies": {
			"angular": "~1.0.7",
			"json3": "~3.2.4",
			"jquery": "~1.9.1",
			"bootstrap-sass": "~2.3.1",
			"es5-shim": "~2.0.8",
			"angular-resource": "~1.0.7",
			"angular-cookies": "~1.0.7",
			"angular-sanitize": "~1.0.7"
		  },
		  "devDependencies": {
			"angular-mocks": "~1.0.7",
			"angular-scenario": "~1.0.7"
		  }
		}
		
		After removing the dependencies and devDependencies :
		-------------------------------------------------------
		{
		  "name": "BaseProject",
		  "version": "0.0.0"
		}


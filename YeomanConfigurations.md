Fresh Installation of Yeoman

	1. Download Node.js from http://nodejs.org/ , install and add to path 

	2. Download GIT from http://git-scm.com/, install  and add to path

	3. configure git using command : git config --global url."https://".insteadOf git://

	4. Download Ruby from https://www.ruby-lang.org/en/, install  and add to path

	5. Install sass using this command: gem install sass --version "3.2.10"

	6. Install compass using this command : gem install compass --version "0.12.2" 
		
	7. Install generators using these commands
	   npm install -g yo
	   npm install -g grunt-cli
	   npm install -g bower
	   npm install -g generator-webapp

	8. Create a folder, go into it and run command
	   yo angular.
	

If already Installed

	1. Configure git using command  
		git config --global url."https://".insteadOf git://

	2. Run commands to clean npm and bower
	   npm cache clean
	   bower cache clean

	3. Run commands to uninstall Compass and sass 
	   gem uninstall compass
	   gem uninstall sass

	4. Run commands to install sass and compass the following versions
	   gem install sass --version "3.2.10"
	   gem install compass --version "0.12.2" 

	5. Install generators using these commands
	   npm install -g yo
	   npm install -g grunt-cli
	   npm install -g bower
	   npm install -g generator-webapp

	6. Create a folder, go into it and run command: yo angular.

	7. Once step 6 is done run command: grunt serve

Grunt build using Maven 

	1. Add this plugin in the ui project pom.xml
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
			<packagingExcludes>WEB-INF/lib/*.jar</packagingExcludes>
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


# Maven configurations

#### Pointing to maven repository

== TODO

#### Java Runtime Version Configuration

    <build>
	 <pluginManagement>
	  <plugins>
	   <plugin>
	    <artifactId>maven-compiler-plugin</artifactId>
	    <groupId>org.apache.maven.plugins</groupId>
	    <version>${maven.compiler.plugin.version}</version>
	    <configuration>
	     <source>${java.source.version}</source>
	     <target>${java.target.version}</target>
	    </configuration>
	   </plugin>
	  </plugins>
	 </pluginManagement>
	</build>
	<properties>
	 <java.source.version>1.7</java.source.version>
	 <java.target.version>1.7</java.target.version>
	 <maven.compiler.plugin.version>2.3.2</maven.compiler.plugin.version>
	</properties>



#### Maven Profiles configuration
###### Profile Configuration
In the current project or in parent project, just configure the following profiles :

	<profiles>
		<profile>
			<id>local</id>
			<activation>
				<activeByDefault>true</activeByDefault>
			</activation>
			<properties>
				<build.profile.id>local</build.profile.id>
			
			 <skip.integration.tests>false</skip.integration.tests>
				<skip.unit.tests>false</skip.unit.tests>
			</properties>
		</profile>
		<profile>
			<id>dev</id>
			<properties>
				<build.profile.id>dev</build.profile.id>
				<skip.integration.tests>false</skip.integration.tests>
				<skip.unit.tests>false</skip.unit.tests>
			</properties>
		</profile>
		<profile>
			<id>qa</id>
			<properties>
				<build.profile.id>qa</build.profile.id>
				<skip.integration.tests>true</skip.integration.tests>
				<skip.unit.tests>true</skip.unit.tests>
			</properties>
		</profile>
	</profiles>



In the current project or child projects, just follow the below two rules:

 i. Configure the filter resources

ii. Add the profiles folder and the profile specific config.properties


####Cofigure the filter resources

    <build>
		<finalName>template-core</finalName>
		<filters>
			<filter>profiles/${build.profile.id}/config.properties</filter>
		</filters>
		<resources>
			<resource>
				<filtering>true</filtering>
				<directory>src/main/resources</directory>
			</resource>
		</resources>
	</build>
	
####Add the profiles folder and the profile specific config.properties
First, I created profiles directory under the project’s root directory. After that was done I created directories called local, dev and qa. These directories contain the actual configuration files, which I created after I had created the directories. The configuration files follow the syntax of normal properties files.

An example of the contents of a configuration file(config.properties) is given in following (for dev profile):

	
    log.filename=logs/dev.log

####Using the profile variables

Example :

In the all the resource directory you mention for filtering, you can use profile variables as:

    ${log.filename}
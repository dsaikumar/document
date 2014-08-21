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
	
	
# springboot-react

 package.json:
"proxy": "http://localhost:8080"


Pom.xml

<plugin>
		<groupId>com.github.eirslett</groupId>
		<artifactId>frontend-maven-plugin</artifactId>
		<version>1.6</version>
		<configuration>
			<workingDirectory>demoreactapp</workingDirectory>--------> Change the react project name
			<installDirectory>target</installDirectory>
		</configuration>
		<executions>
			<execution>
				<id>install node and npm</id>
				<goals>
					<goal>install-node-and-npm</goal>
				</goals>
				<configuration>
					<nodeVersion>v8.9.4</nodeVersion> -> change your node & npm version 
					<npmVersion>5.6.0</npmVersion>
				</configuration>
			</execution>
			<execution>
				<id>npm install</id>
				<goals>
					<goal>npm</goal>
				</goals>
				<configuration>
					<arguments>install</arguments>
				</configuration>
			</execution>
			<execution>
				<id>npm run build</id>
				<goals>
					<goal>npm</goal>
				</goals>
				<configuration>
					<arguments>run build</arguments>
				</configuration>
			</execution>
		</executions>
	</plugin>
  
  <plugin>
		<artifactId>maven-antrun-plugin</artifactId>
		<executions>
			<execution>
				<phase>generate-resources</phase>
				<configuration>
					<target>
						<copy todir="${project.build.directory}/classes/public">
							<fileset dir="${project.basedir}/frontend/build"/>
						</copy>
					</target>
				</configuration>
				<goals>
					<goal>run</goal>
				</goals>
			</execution>
		</executions>
	</plugin>

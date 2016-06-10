# IFM Catalog BOM  (Bill of Materials)

## Introduction
Maven dependencies in project poms can be controlled by importing a project that declares dependencies.  This project defines the versions we use across IFM projects.

## Using in a project pom
To use this BOM, do the following in your project.

In <properties> define the version of the BOM to import.
```
<properties>
		<ifm.bom.version>0.2-SNAPSHOT</ifm.bom.version>
```

Add the following to <dependencies>
```
		<dependency>
			<groupId>mil.nasic.catalog</groupId>
			<artifactId>bom</artifactId>
			<version>${ifm.bom.version}</version>
			<type>pom</type>
			<scope>import</scope>
		</dependency>
```

Now for all your other dependencies, remove the version, and let the BOM aide us in dependency convergence:
```
		<dependency>
			<groupId>com.fasterxml.jackson.core</groupId>
			<artifactId>jackson-databind</artifactId>
			[NO VERSION]
		</dependency>
```


## Problems
Eclipse interprets no version in dependencies as an error in your pom.  There does not appear to be a way to disable this error.  
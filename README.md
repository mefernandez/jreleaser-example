# What

This is an example project to showcase how to release a Maven multi-module project with `maven-release-plugin` and `jreleaser-maven-plugin`.
It chains both _plugins_ to achieve a full release with everything both plugins can do.

The secret sauce is to tell `maven-release-plugin` to call `jreleaser-maven-plugin` mid-way:

```xml
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-release-plugin</artifactId>
				<version>3.0.0-M6</version>
				<configuration>
					<preparationGoals>jreleaser:full-release</preparationGoals>
				</configuration>
			</plugin>
```

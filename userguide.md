## Using OWASP Dependency Check

Once you have OWASP Dependency Check installed, you can easily run it against your project to detect vulnerabilities within your dependencies.

### Execution Commands

For the standalone JAR, execute the following command:

```sh
java -jar dependency-check.jar --project <project-name> --scan <path-to-project>
```

For Maven, simply run:

```sh
mvn dependency-check:check
```

Ensure to replace `<project-name>` with your project's name and `<path-to-project>` with the actual directory path.

### Configuration

OWASP Dependency Check provides a range of configuration options that allow you to tailor its behavior to your specific requirements. Refer to the Configuration Guide for comprehensive details on how to customize the tool's settings.

### Reporting

OWASP Dependency Check generates detailed reports outlining the vulnerabilities identified within your project's dependencies. Locate the generated reports at the following locations:

- For the standalone JAR: `<path-to-project>/target/dependency-check-report.html`
- For Maven: `<path-to-project>/target/dependency-check-report.html`
- For Gradle: `<path-to-project>/build/reports/dependency-check-report.html`

Open the HTML report using your preferred web browser to access in-depth vulnerability details.

### Contributing

Should you encounter any issues or wish to contribute to OWASP Dependency Check, please consult the Contributing Guidelines for guidance on how to engage and participate.

### Resources

For additional information and resources, explore the following links:

- [OWASP Dependency Check GitHub Repository](https://github.com/jeremylong/DependencyCheck)
- [OWASP Dependency Check Official Website](https://owasp.org/www-project-dependency-check/)

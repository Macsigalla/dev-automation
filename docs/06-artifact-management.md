
# 6. Artifact Management Using Nexus

## 6.1 Introduction

Nexus Repository Manager is used to store and manage application build artifacts.

It provides a centralized location for publishing, retrieving, and managing software packages generated during the CI/CD process.

## 6.2 Purpose of Artifact Management

Artifact management provides:

- Centralized storage of build outputs.
- Version management.
- Controlled artifact distribution.
- Build traceability.
- Consistent deployment packages.

## 6.3 Nexus Repository Types

The project can use the following Maven repository types:

### Maven Hosted Repository

Stores internally generated application artifacts.

### Maven Proxy Repository

Caches dependencies retrieved from external repositories.

### Maven Group Repository

Combines multiple repositories into a single access endpoint.

## 6.4 Jenkins Integration

Jenkins integrates with Nexus to publish successful Maven build artifacts.

The integration uses securely configured repository credentials.

## 6.5 Artifact Publishing Workflow

1. Jenkins checks out application source code.
2. Maven compiles and tests the application.
3. Maven packages the application.
4. Jenkins publishes the artifact to Nexus.
5. The artifact is stored with its version information.
6. Approved artifacts can be retrieved for subsequent deployment.

## 6.6 Maven Packaging

Example command:

```bash
mvn clean package
```

The generated application package is typically located inside:

```text
target/
```

## 6.7 Artifact Versioning

Artifacts should use consistent version numbers to support traceability and controlled releases.

For example:

```text
app-1.0.0.war
app-1.0.1.war
app-1.1.0.war
```

Actual artifact names depend on the Maven project configuration.

## 6.8 Security Considerations

- Protect Nexus administrative access.
- Use dedicated repository credentials.
- Avoid hardcoding passwords.
- Restrict repository permissions.
- Maintain artifact retention policies.

## 6.9 Conclusion

Nexus provides centralized artifact storage and improves the reliability and traceability of application build and release processes.

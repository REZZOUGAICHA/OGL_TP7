# CI/CD Project - Gradle App

## Overview

A simple CI/CD pipeline using Jenkins and Gradle for educational purposes.
- `Jenkinsfile`: Pipeline definition

## CI/CD Stages

1. **Test**: Run tests and archive reports.
2. **Code Analysis**: Analyze with SonarQube.
3. **Quality Check**: Verify SonarQube quality gate.
4. **Build**: Create JAR and Javadoc.
5. **Deploy**: Publish JAR (configure repo).
6. **Notify**: Send email/Slack alerts.

## Prerequisites

- Jenkins, Gradle, SonarQube
- SonarQube token in Jenkins (`SONAR_AUTH_TOKEN`)
- Slack integration


## Notes

Demonstrates CI/CD principles and "Pipeline as Code."

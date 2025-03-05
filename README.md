# SonarQube Setup with Docker Compose

## Setup
Start two containers using:

```bash
docker compose up
```

The SonarQube service along with the database will start on the latest platforms.

Wait for SonarQube to initialize, then log in to the portal with the default credentials:

**Username:** `admin`
**Password:** `admin`

Open the portal in your browser:

```url
http://localhost:9000
```

After a successful login, you will be prompted to change the admin password for security reasons.

## Creating a Local Project

1. Create a new project and enter its name and key (it will be automatically generated from the name).
2. Use global settings.
3. Choose the analysis method as **local**.

Insert the generated key and token into the `sonar-project.properties` file:

```properties
sonar.projectKey=<your-project-key>
sonar.projectName=<project-name>
sonar.sources=.
sonar.host.url=http://portal:9123
sonar.login=<your-token>
```

You can configure many additional options in the `sonar-project.properties` file. For more details, refer to the [official documentation](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/).

## Running the Analysis

```bash
docker compose up scanner
```

Once the analysis is complete, you can view the results in the SonarQube portal.

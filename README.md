# OpenMRS 3.0 Reference Application

This project holds the build configuration for the OpenMRS 3.0 reference application, found on
https://dev3.openmrs.org and https://o3.openmrs.org.

## Quick start

### Update the distribution and prepare the run

```
docker compose -f docker-compose-ohri-[dev | namibia | working ].yml pull
```

### Run the Selected Distro

```
docker compose -f docker-compose-ohri-[dev | namibia | working ].yml  up
```

New OpenMRS UI is accessible at http://localhost/openmrs/spa

OpenMRS Legacy UI is accessible at http://localhost/openmrs

## Overview

This distribution consists of four images:

- db - This is just the standard MariaDB image supplied to use as a database
- backend - This image is the OpenMRS backend. It is built from the main Dockerfile included in the root of the project and
  based on the core OpenMRS Docker file. Additional contents for this image are drawn from the `distro` sub-directory which
  includes a full Initializer configuration for the reference application intended as a starting point.
- frontend - This image is a simple nginx container that embeds the 3.x frontend, including the modules described in the
  `frontend/spa-build-config.json` file.
- proxy - This image is an even simpler nginx reverse proxy that sits in front of the `backend` and `frontend` containers
  and provides a common interface to both. Basically, this help mitigate CORS issues.

## Contributing to the configuration

Thanks!

# OpenAPI generated server

## Overview
This server was generated by the [OpenAPI Generator](https://openapi-generator.tech) project. By using the
[OpenAPI-Spec](https://openapis.org) from a remote server, you can easily generate a server stub.  This
is an example of building a OpenAPI-enabled Flask server.

This example uses the [Connexion](https://github.com/zalando/connexion) library on top of Flask.

## Requirements
Python 3.5.2+

## Usage
To run the development server, please execute the following from the root directory:

```
pip3 install -r requirements.txt
python3 -m pfeffernusse
```

and open your browser to here:

```
http://localhost:8080/v1/ui/
```

Your OpenAPI definition lives here:

```
http://localhost:8080/v1/openapi.json
```

To run the production server locally please execute the following from the root directory:
```
pip3 install -r requirements.txt
gunicorn --bind 0.0.0.0:8080 pfeffernusse.wsgi
```

## Running with Docker

To run the server on a Docker container, please execute the following from the root directory:

```bash
# building the image
docker build -t pfeffernusse .

# starting up a container
docker run -p 8080:8080 pfeffernusse
```

The Docker container runs pfeffernusse using gunicorn.

## OpenAPI Specification
We maintain a versioned specification via the USGS Astro SwaggerHub organization. The current version of the specification is available at: https://app.swaggerhub.com/apis/USGS-Astro/pfeffernusse2/0.1.4-oas3

## Writing a driver
Documentation on adding to or extending an existing driver is available via the wiki at https://github.com/USGS-Astrogeology/pfeffernusse/wiki/Writing-New-Drivers.

We currently support:

| Mission | Instrument | Data Format(s) |
| ------- |:----------:|:--------------:|
| Messenger | MDIS-NAC  | PDS3 EDR      |
| Messenger | MDIS-WAC  | PDS3 EDR      |
| MRO     | CTX | PDS3 EDR |
| LRO | NAC | PDS3 EDR|
| LRO | WAC | PDS3 EDR|
| Cassini | ISS-NAC* | PDS3 EDR|
| Cassini | ISS-WAC* | PSD3 EDR|

* These instruments are supported via pfeffernusse, but not yet supported by the USGS [Community Sensor Model](https://github.com/USGS-Astrogeology/CSM-CameraModel)

## Code Generation
The following section assumes installation of the command line utility `openapi-generator` rather than
the similarly named `openapi-generator-cli`.  It appears that these utilities provide
the same functionality under different names.  If you've installed openapi-generator-cli, then
it will be necessary to modify the makefile.

To regenerate the auto-generated portions of the code base, it is necessary to have the `openapi-generator` installed. Installation instructions are available [here](https://github.com/OpenAPITools/openapi-generator#1---installation).  Once installed, simply run `make server` to (re)generate the autogenerated components. This is generally only used when testing changes to the specification locally before publishing them.

Alternatively, run `openapi-generator generate -g python-flask -i pfeffernusse/openapi/openapi.yaml --api-package pfeffernusse`

By default, files are generated into the current working directory.  The following
files are generated:
  - openapi_generator/VERSION
  - openapi_server/*
  - .dockerignore
  - .gitignore
  - .travis.yml
  - git_push.sh
  - test-requirements.txt
  - tox.ini

After generating the code, it is necessary to make the following adjustment(s):
  - rename openapi-server/ to pfeffernusse/ (directories)

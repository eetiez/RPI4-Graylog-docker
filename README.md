# RPI4-Graylog-docker

This repository contains files to run a Graylog instance on Raspberry Pi 4.

## Objective

The Raspberry Pi 4 has been released with an ARM64v8 CPU and can be purchased with 4 or even 8 Go of memory. As a result, it makes possible to run services on it which were almost impossible to run on former versions mainly due to the low memory available. Furthermore, several OS running on Raspberry Pi 4 are now available with 64-bit versions.

The objective was to create with the Raspberry Pi 4 a Graylog instance running on dockers. The files needed to create it are available on this repository. The objective was to stick as possible to the Dockerfiles furnished by the differents projects.

## Problems

Graylog container is unfortunately not available for ARM64v8. It is then needed to be recreated from scratch. It uses `openjdk:8-jre-slim-buster` container which is also not available for ARM64v8. It also has to be recreated from scratch.

Graylog needs Elasticsearch to work. The good news is that Elasticsearch 7.x official containers are available for ARM64v8. The bad news is that Graylog is not compatble with Elasticsearch 7.x as mentioned in the documentation. As there are no official Elasticsearch 6.x containers, an Elasticsearch 6.8.12 container has also been recreated from scratch.

Finally, Graylog needs MongoDB to store its configuration files. Luckily, MongoDB official containers are available for ARM64v8. According to Graylog's documentation, as it is compatbile with MongoDB 3.6, 4.0 and 4.2, the `mongo:4.2` container has been chosen for this project.
# TAAP Content

## Learning Objectives

In this unit you will:

- Describe T-Mobile’s API Access Process (TAAP) in relation to Zero-Trust philosophy.
- Work with the TAAP library in the context of securing a simple Java Spring Boot application.

You'll know you're ready to move on when you can complete this lesson's [checkpoint](./03-checkpoint.md).

## Pre-Requisites for the Checkpoint

- You must be connected to the T-Mobile VPN
- You must have Docker version 18.09 or greater
  - Run `$ docker version` to find out if your output looks like this: 
    ```
    Client: Docker Engine - Community
    Cloud integration  0.1.18
    Version:           19.03.13
    ...
    ```
    If the `Version` field returns a number greater than `18.09`, you are in business
- You must be able to see the [DevCenter exercise instructions](https://devcenter.t-mobile.com/documents/5ea1eb3f4943485a603dc382/5ea1eb3f4943485a603dc380?name=API-Security-Workshop&sectionName=2.0-Implement-TAAP-Security-for-Spring-Boot-Microservices)
- You should be able to access [Artifactory](https://artifactory.cdp.t-mobile.com/)
  - Watch [this video](https://www.youtube.com/watch?v=GyBiuvjNMG0) to learn about how to access it
- You should be a Java developer
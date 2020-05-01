# kabanero-stack-hub

A stack hub is the central control point for application stacks that you want to use in your organization. These stacks might be clones of public stacks or they might be customized to meet local requirements. For example, you might want to include templates with unique starter applications, specify a different test framework, or ensure that your applications are developed on specific software levels.

Before building a stack hub you should identify the stacks that you want to use for developing your microservice applications. Clone the available stacks and make any modifications that are needed. How to customize, package, and publish stacks is covered in the [Customizing applications stacks](https://kabanero.io/guides/working-with-stacks/) guide.

The [Creating a stack hub](https://kabanero.io/guides/creating-a-stack-hub/) guide will cover how to build a stack hub that consolidates multiple application stacks for use in your organization, how to release your stack hub in GitHub, and how to use the assets in your deployment environment.

## Adding a new stack
If you wish to add a new stack to the default Kabanero stack hub please open a PR against the relevant releae branch or against the master branch for future releases.

Your PR needs to update the `config/default_kabanero_config.yaml` with a reference to the remote index for your stack. You can use the filtering capabilites available in repo-tools if the index contains more than one stack, see the [repo tools](https://github.com/appsody/repo-tools) repository for further details.

## Stack requirements
Any stack included in the Kabanero stack hub is required to pass a certification process. When a PR is opened to add a new stack part of the review process will involve ensuring the stacks base container image meets the certification requirements that are detailed below.

## Stack certification criteria

    1- Container must be use a Red Hat base image:

    The image must be UBI basedand where possible be a RedHat Runtimes image.

    2 - Container images should include RPM packages from Red Hat Universal Base Image (UBI) repositories only.

    3 - The following metadata must be included in the container image:

    name: Name of the image
    vendor: Company name 
    version: Version of the image 
    release: A number used to identify the specific build for this image 
    summary: A short overview of the application or component in this image
    description:  A long description of the application or component in this image 

    4 - No modifications should be made to content provided by Red Hat packages or layers, except for files that are meant to be modified by end users, such as configuration files.

    5 - The container image cannot contain any critical or important vulnerabilities, as defined at https://access.redhat.com/security/updates/classification

    6 - No modification, replacement or combination of the Red Hat base layer(s) should be made.

    7 - The container image should have less than 40 layers when uncompressed.

    8 - The image should always be tagged with a version other than latest.

    9 - The image must include software terms and conditions.

    Create a directory named /licenses and include all relevant licensing and/or terms and conditions as text file(s) in that directory.

    10 - The image should not run as the root user.

    11 - The image should not request host-level privileges.

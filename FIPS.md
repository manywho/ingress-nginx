FIPS Mode
=========

To build an image that runs the ingress controller in FIPS mode, follow these steps:

1. First, we need to set the Docker registry name that we want to end up pushing the images to. This should just be the top levels, as the last segment is appended by the following steps.

    ```bash
    $ export REGISTRY=quay.io/manywho
    ```

1. Enter into the `nginx` image directory, and compile, build and push the image, which will be used as the base image later:

    ```bash
    $ cd images/nginx
    $ make push
    ```

1. Finally, compile, build and push the ingress image:

    ```bash
    $ cd ../../
    $ BASEIMAGE=quay.io/manywho/nginx:0.81 make build container push
    ```
# Opentelemetry collector builder
Create a custom opentelemetry collector image

## Automated way :tada:
Using [a custom otelcol builder](https://github.com/martinjt/ocb-config-builder)

1. create a branch with a specific otel config file
2. push to this branch
3. wait for the github actions to finish
4. the image will be pushed to ghcr with the branch name on it

## Legacy way
The """"old"""" way

### Build the otelcol binary in local

1. go to /legacy
2. create a [custom manifest file](https://opentelemetry.io/docs/collector/custom-collector/#step-2---create-a-builder-manifest-file) & a custom otelcol config file
3. add your custom otel config file
4. Build your custom otelcol binary
```shell
./ocb --config YOUR_MANIFEST_FILE
```
5. go to the folder generated and run your custom otelcol
```shell
./YOUR_GENERATED_FOLDER/YOUR_OTELCOL_BINARY --config YOUR_CONFIG_FILE
```

### Build via the Dockerfile

1. go to /legacy
2. create a [custom manifest file](https://opentelemetry.io/docs/collector/custom-collector/#step-2---create-a-builder-manifest-file) & a custom otelcol config file
3. Update the `Dockerfile` with the right manifest & config files
4. build your custom otelcol image
```shell
docker build . -t "<YOUR_OTELCOL_IMAGE_NAME>"
```
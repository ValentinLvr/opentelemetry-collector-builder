FROM golang:1.21 as build
ARG  OTEL_VERSION=0.90.1
WORKDIR /app
RUN go install go.opentelemetry.io/collector/cmd/builder@v${OTEL_VERSION}
COPY . .
RUN CGO_ENABLED=0 builder --config=basic-manifest.yml --output-path=/app
 
FROM cgr.dev/chainguard/static:latest
COPY --from=build /app/otelcol-custom /
COPY basic-config.yml /
EXPOSE 4317/tcp 4318/tcp 13133/tcp
 
CMD ["/otelcol-custom", "--config=/basic-config.yml"]
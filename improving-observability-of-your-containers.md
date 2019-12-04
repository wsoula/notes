Improving Container Observability
---
* full stack visbility
  * application level - each service, between services
  * container service level - service, tasks, pods
  * compute service level

Compatibility with existing toolsets
* aws-managed
* apn partner - datadog
* self-managed - prometheus

Run anywhere wiothout changing tools

AWS App Mesh, FireLens & AWS Fluent Bit, something else

App Mesh - aws service mesh

Per service dashboard
Service to service dashboards
Tracing dashborads

Per saervice dashboard - top services with requests, latency, top services with errors
service to service - idk.  Could be counting requests to service A that go to service B and then couting requests to service B from service A and make sure they are the same

FireLens - send logs natively to AWS or any partner (datadog), send logs to cold storage and pull on demand to analytics tools (Athena?)

AWS fir FluentBit container can run anywhere (ECS, EKS, fargate)

container insights works across ECS, EKS, FarGate
  * fully managed observability service for monitoring, troubleshooting, and alarmsing
    * reliable, secure metrics and logs collection
    * automated summaries and analysis
    * observability experience across metrics, logs, traces
    * pre-created dashboards

 debugging
   * infra - cluster cpu, memeory
   * container - service taks count, task/pod memory utilization
   * application - log insights querying for (errors?)

 apache bench

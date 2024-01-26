---
title: "Fluent Bit in Local Machine"
date: 2024-01-26T20:07:59+05:30
---


## What is Fluent Bit

> Official defenition
>
> Fluent Bit is a lightweight open-source telemetry agent specifically designed to efficiently handle the challenges of collecting and processing telemetry data across a wide range of environments, from constrained systems to complex cloud infrastructures. 

**Whoops...** Let me simplify that definition.

Fluent Bit is lightweight Log Processor gathers information from various sources, utilizes Parsers and Filters to process the collected data, and then sends the processed information to mutliple storages. 

![Alt Text](/img/image.png)


I am using Ubuntu. I will cover how to do same using docker image in future.

```go
curl https://raw.githubusercontent.com/fluent/fluent-bit/master/install.sh | sh
```

and run below command to start

```bash
sudo systemctl start fluent-bit
sudo systemctl status fluent-bit 
```


![Alt Text](/img/image-1.png)

## How to test

Save the following snippet in your directory. After that run below command.

```bash
/opt/fluent-bit/bin/fluent-bit -c fluentbit-logs-3.yaml

```


**sample.log**
```yaml
log_level=INFO timestamp=2024-01-04T09:43:45.171 product=APP service=myapp server_name=myapp_backend environment=development end -> Message 1
log_level=INFO timestamp=2024-01-04T09:43:45.172 product=APP service=myapp server_name=myapp_backend environment=development end -> Message 2
      "lllll": true,
      "time_in_force": true
    }), ABCDTO(name=stop_limit, allowedProperties={
      "lllll": true,
      "time_in_force": true
    }), ABCDTO(name=app, allowedProperties={})], status=active, collar=6.00, feeType=flat, makerFee=30, takerFee=40, priceDecimalPlaces=2, quantityDecimalPlaces=8, marketCapPercentage=5)),[]>}, duration(ms): 44 ms
log_level=INFO timestamp=2024-01-04T09:43:45.486 product=APP service=myapp server_name=myapp_backend environment=development start -> Executing GuidedTourController.fetchGuidedTourDetails()
log_level=INFO timestamp=2024-01-04T09:43:45.489 product=APP service=myapp server_name=myapp_backend environment=development end -> Finished executing: GuidedTourController.fetchGuidedTourDetails() clientIP = 10.64.1.248,methodType: GET, requestURI:/v1/private/tours ,{"path": "file:/app.jar!/BOOT-INF/classes!/in/APP/myapp/guidedtour/controller/","code_file_name":"GuidedTourController", "method_name": "fetchGuidedTourDetails", "code_file_line": "empty" , "payload": <200 OK OK,GenericSuccessResponseDTO(status=Success, message=guided_tour_details_fetched_successfully, data=FetchGuidedTourResponseDTO(guidedTour=GuidedTourData(web={is_pro_trade_visited=true, is_footer_tab_visited=true, is_lite_trade_visited=true}, mobile={}))),[]>}, duration(ms): 3 ms
log_level=INFO timestamp=2024-01-04T09:43:45.489 server_name=myapp_backend environment=development end -> Finished executing: GuidedTourController.fetchGuidedTourDetails() clientIP = 10.64.1.248,methodType: GET, requestURI:/v1/private/tours ,{"path": "file:/app.jar!/BOOT-INF/classes!/in/APP/myapp/guidedtour/controller/","code_file_name":"GuidedTourController", "method_name": "fetchGuidedTourDetails", "code_file_line": "empty" , "payload": <200 OK OK,GenericSuccessResponseDTO(status=Success, message=guided_tour_details_fetched_successfully, data=FetchGuidedTourResponseDTO(guidedTour=GuidedTourData(web={is_pro_trade_visited=true, is_footer_tab_visited=true, is_lite_trade_visited=true}, mobile={}))),[]>}, duration(ms): 3 ms
log_level=INFO timestamp=2024-01-04T09:39:30.506 product=APP service=myapp server_name=myapp_backend environment=development Exception while fetching activity location with message:org.springframework.web.reactive.function.client.WebClientRequestException: readAddress(..) failed: Connection reset by peer; nested exception is io.netty.channel.unix.Errors$NativeIoException: readAddress(..) failed: Connection reset by peer
	at org.springframework.web.reactive.function.client.AppFunctions$DefaultExchangeFunction.lambda$wrapException$9(AppFunctions.java:141)
	Suppressed: reactor.core.publisher.FluxOnAssembly$OnAssemblyException: Error has been observed at the following site(s):
	*__checkpoint ⇢ Request to GET [DefaultWebClient] Original Stack Trace:
        at org.springframework.web.reactive.function.client.AppFunctions$DefaultExchangeFunction.lambda$wrapException$9(AppFunctions.java:141)
		at reactor.core.publisher.MonoErrorSupplied.subscribe(MonoErrorSupplied.java:55)
		at reactor.core.publisher.Mono.subscribe(Mono.java:4400)
		at reactor.core.publisher.FluxOnErrorResume$ResumeSubscriber.onError(FluxOnErrorResume.java:103)
		at reactor.core.publisher.FluxPeek$PeekSubscriber.onError(FluxPeek.java:222)
		at reactor.core.publisher.FluxPeek$PeekSubscriber.onError(FluxPeek.java:222)
		at reactor.core.publisher.FluxPeek$PeekSubscriber.onError(FluxPeek.java:222)
		at reactor.core.publisher.MonoNext$NextSubscriber.onError(MonoNext.java:93)
		at reactor.core.publisher.MonoFlatMapMany$FlatMapManyMain.onError(MonoFlatMapMany.java:204)
		at reactor.core.publisher.SerializedSubscriber.onError(SerializedSubscriber.java:124)
		at reactor.core.publisher.FluxRetryWhen$RetryWhenMainSubscriber.whenError(FluxRetryWhen.java:225)
		at reactor.core.publisher.FluxRetryWhen$RetryWhenOtherSubscriber.onError(FluxRetryWhen.java:274)
		at reactor.core.publisher.FluxConcatMap$ConcatMapImmediate.drain(FluxConcatMap.java:415)
		at reactor.core.publisher.FluxConcatMap$ConcatMapImmediate.onNext(FluxConcatMap.java:251)
		at reactor.core.publisher.EmitterProcessor.drain(EmitterProcessor.java:491)
		at reactor.core.publisher.EmitterProcessor.tryEmitNext(EmitterProcessor.java:299)
		at reactor.core.publisher.SinkManySerialized.tryEmitNext(SinkManySerialized.java:100)
		at reactor.core.publisher.InternalManySink.emitNext(InternalManySink.java:27)
		at reactor.core.publisher.FluxRetryWhen$RetryWhenMainSubscriber.onError(FluxRetryWhen.java:190)
		at reactor.core.publisher.MonoCreate$DefaultMonoSink.error(MonoCreate.java:194)
		at reactor.netty.http.client.HttpClientConnect$HttpObserver.onUncaughtException(HttpClientConnect.java:384)
		at reactor.netty.ReactorNetty$CompositeConnectionObserver.onUncaughtException(ReactorNetty.java:670)
		at reactor.netty.resources.DefaultPooledConnectionProvider$DisposableAcquire.onUncaughtException(DefaultPooledConnectionProvider.java:202)
		at reactor.netty.resources.DefaultPooledConnectionProvider$PooledConnection.onUncaughtException(DefaultPooledConnectionProvider.java:450)
		at reactor.netty.channel.FluxReceive.drainReceiver(FluxReceive.java:232)
		at reactor.netty.channel.FluxReceive.onInboundError(FluxReceive.java:453)
		at reactor.netty.channel.ChannelOperations.onInboundError(ChannelOperations.java:488)
		at reactor.netty.channel.ChannelOperationsHandler.exceptionCaught(ChannelOperationsHandler.java:126)


```

**parsers.conf**
```yaml
# parsers.conf

[MULTILINE_PARSER]
    name          multiline-regex-test
    type          regex
    flush_timeout 1000
    #
    # Regex rules for multiline parsing
    # ---------------------------------
    #
    # configuration hints:
    #
    #  - first state always has the name: start_state
    #  - every field in the rule must be inside double quotes
    #
    # rules |   state name  | regex pattern                  | next state
    # ------|---------------|--------------------------------------------
    rule      "start_state"   "/log_level=(\w+)\s+timestamp=(\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}.\d{3})\s+product=(\w+)\s+service=(\w+)\s+server_name=(\w+)\s+environment=(\w+)\s+(.+)/"  "cont"
    rule      "cont"          "/^\s+.*/"                     "cont"

[PARSER]
    Name   apache
    Format regex
    Regex  ^(?<host>[^ ]*) [^ ]* (?<user>[^ ]*) \[(?<time>[^\]]*)\] "(?<method>\S+)(?: +(?<path>[^\"]*?)(?: +\S*)?)?" (?<code>[^ ]*) (?<size>[^ ]*)(?: "(?<referer>[^\"]*)" "(?<agent>[^\"]*)")?$
    Time_Key time
    Time_Format %d/%b/%Y:%H:%M:%S %z

[PARSER]
    Name   apache2
    Format regex
    Regex  ^(?<host>[^ ]*) [^ ]* (?<user>[^ ]*) \[(?<time>[^\]]*)\] "(?<method>\S+)(?: +(?<path>[^ ]*) +\S*)?" (?<code>[^ ]*) (?<size>[^ ]*)(?: "(?<referer>[^\"]*)" "(?<agent>.*)")?$
    Time_Key time
    Time_Format %d/%b/%Y:%H:%M:%S %z

[PARSER]
    Name   apache_error
    Format regex
    Regex  ^\[[^ ]* (?<time>[^\]]*)\] \[(?<level>[^\]]*)\](?: \[pid (?<pid>[^\]]*)\])?( \[client (?<client>[^\]]*)\])? (?<message>.*)$

[PARSER]
    Name   nginx
    Format regex
    Regex ^(?<remote>[^ ]*) (?<host>[^ ]*) (?<user>[^ ]*) \[(?<time>[^\]]*)\] "(?<method>\S+)(?: +(?<path>[^\"]*?)(?: +\S*)?)?" (?<code>[^ ]*) (?<size>[^ ]*)(?: "(?<referer>[^\"]*)" "(?<agent>[^\"]*)")
    Time_Key time
    Time_Format %d/%b/%Y:%H:%M:%S %z

[PARSER]
    # https://rubular.com/r/IhIbCAIs7ImOkc
    Name        k8s-nginx-ingress
    Format      regex
    Regex       ^(?<host>[^ ]*) - (?<user>[^ ]*) \[(?<time>[^\]]*)\] "(?<method>\S+)(?: +(?<path>[^\"]*?)(?: +\S*)?)?" (?<code>[^ ]*) (?<size>[^ ]*) "(?<referer>[^\"]*)" "(?<agent>[^\"]*)" (?<request_length>[^ ]*) (?<request_time>[^ ]*) \[(?<proxy_upstream_name>[^ ]*)\] (\[(?<proxy_alternative_upstream_name>[^ ]*)\] )?(?<upstream_addr>[^ ]*) (?<upstream_response_length>[^ ]*) (?<upstream_response_time>[^ ]*) (?<upstream_status>[^ ]*) (?<reg_id>[^ ]*).*$
    Time_Key    time
    Time_Format %d/%b/%Y:%H:%M:%S %z

[PARSER]
    Name   json
    Format json
    Time_Key time
    Time_Format %d/%b/%Y:%H:%M:%S %z

[PARSER]
    Name   logfmt
    Format logfmt

[PARSER]
    Name         docker
    Format       json
    Time_Key     time
    Time_Format  %Y-%m-%dT%H:%M:%S.%L
    Time_Keep    On
    # --
    # Since Fluent Bit v1.2, if you are parsing Docker logs and using
    # the Kubernetes filter, it's not longer required to decode the
    # 'log' key.
    #
    # Command      |  Decoder | Field | Optional Action
    # =============|==================|=================
    #Decode_Field_As    json     log

[PARSER]
    Name        docker-daemon
    Format      regex
    Regex       time="(?<time>[^ ]*)" level=(?<level>[^ ]*) msg="(?<msg>[^ ].*)"
    Time_Key    time
    Time_Format %Y-%m-%dT%H:%M:%S.%L
    Time_Keep   On

[PARSER]
    Name        syslog-rfc5424
    Format      regex
    Regex       ^\<(?<pri>[0-9]{1,5})\>1 (?<time>[^ ]+) (?<host>[^ ]+) (?<ident>[^ ]+) (?<pid>[-0-9]+) (?<msgid>[^ ]+) (?<extradata>(\[(.*?)\]|-)) (?<message>.+)$
    Time_Key    time
    Time_Format %Y-%m-%dT%H:%M:%S.%L%z
    Time_Keep   On

[PARSER]
    Name        syslog-rfc3164-local
    Format      regex
    Regex       ^\<(?<pri>[0-9]+)\>(?<time>[^ ]* {1,2}[^ ]* [^ ]*) (?<ident>[a-zA-Z0-9_\/\.\-]*)(?:\[(?<pid>[0-9]+)\])?(?:[^\:]*\:)? *(?<message>.*)$
    Time_Key    time
    Time_Format %b %d %H:%M:%S
    Time_Keep   On

[PARSER]
    Name        syslog-rfc3164
    Format      regex
    Regex       /^\<(?<pri>[0-9]+)\>(?<time>[^ ]* {1,2}[^ ]* [^ ]*) (?<host>[^ ]*) (?<ident>[a-zA-Z0-9_\/\.\-]*)(?:\[(?<pid>[0-9]+)\])?(?:[^\:]*\:)? *(?<message>.*)$/
    Time_Key    time
    Time_Format %b %d %H:%M:%S
    Time_Keep   On

[PARSER]
    Name    mongodb
    Format  regex
    Regex   ^(?<time>[^ ]*)\s+(?<severity>\w)\s+(?<component>[^ ]+)\s+\[(?<context>[^\]]+)]\s+(?<message>.*?) *(?<ms>(\d+))?(:?ms)?$
    Time_Format %Y-%m-%dT%H:%M:%S.%L
    Time_Keep   On
    Time_Key time

[PARSER]
    # https://rubular.com/r/0VZmcYcLWMGAp1
    Name    envoy
    Format  regex
    Regex ^\[(?<start_time>[^\]]*)\] "(?<method>\S+)(?: +(?<path>[^\"]*?)(?: +\S*)?)? (?<protocol>\S+)" (?<code>[^ ]*) (?<response_flags>[^ ]*) (?<bytes_received>[^ ]*) (?<bytes_sent>[^ ]*) (?<duration>[^ ]*) (?<x_envoy_upstream_service_time>[^ ]*) "(?<x_forwarded_for>[^ ]*)" "(?<user_agent>[^\"]*)" "(?<request_id>[^\"]*)" "(?<authority>[^ ]*)" "(?<upstream_host>[^ ]*)"
    Time_Format %Y-%m-%dT%H:%M:%S.%L%z
    Time_Keep   On
    Time_Key start_time

[PARSER]
    # https://rubular.com/r/17KGEdDClwiuDG
    Name    istio-envoy-proxy
    Format  regex
    Regex ^\[(?<start_time>[^\]]*)\] "(?<method>\S+)(?: +(?<path>[^\"]*?)(?: +\S*)?)? (?<protocol>\S+)" (?<response_code>[^ ]*) (?<response_flags>[^ ]*) (?<response_code_details>[^ ]*) (?<connection_termination_details>[^ ]*) (?<upstream_transport_failure_reason>[^ ]*) (?<bytes_received>[^ ]*) (?<bytes_sent>[^ ]*) (?<duration>[^ ]*) (?<x_envoy_upstream_service_time>[^ ]*) "(?<x_forwarded_for>[^ ]*)" "(?<user_agent>[^\"]*)" "(?<x_request_id>[^\"]*)" (?<authority>[^ ]*)" "(?<upstream_host>[^ ]*)" (?<upstream_cluster>[^ ]*) (?<upstream_local_address>[^ ]*) (?<downstream_local_address>[^ ]*) (?<downstream_remote_address>[^ ]*) (?<requested_server_name>[^ ]*) (?<route_name>[^  ]*)
    Time_Format %Y-%m-%dT%H:%M:%S.%L%z
    Time_Keep   On
    Time_Key start_time

[PARSER]
    # http://rubular.com/r/tjUt3Awgg4
    Name cri
    Format regex
    Regex ^(?<time>[^ ]+) (?<stream>stdout|stderr) (?<logtag>[^ ]*) (?<message>.*)$
    Time_Key    time
    Time_Format %Y-%m-%dT%H:%M:%S.%L%z
    Time_Keep   On

[PARSER]
    Name    kube-custom
    Format  regex
    Regex   (?<tag>[^.]+)?\.?(?<pod_name>[a-z0-9](?:[-a-z0-9]*[a-z0-9])?(?:\.[a-z0-9]([-a-z0-9]*[a-z0-9])?)*)_(?<namespace_name>[^_]+)_(?<container_name>.+)-(?<docker_id>[a-z0-9]{64})\.log$
```

**fluentbit-logs-3.yaml**
```yaml
# Multiline parsing in Filters
# Add label inside filters
# fluentbit-logs-3.yaml
 
service:
  log_level: info
  parsers_file: parsers.conf
  hot_relaod: on

pipeline:
  inputs:
    - name: tail
      path: <Path-to>/sample.log
      read_from_head: true

  filters:
    - name: multiline
      match: "*"
      multiline.key_content: log
      multiline.parser: multiline-regex-test

    - name: modify
      match: "*"
      add: your_label_name your_label_value


  outputs:
    - name: stdout
      match: '*'
```
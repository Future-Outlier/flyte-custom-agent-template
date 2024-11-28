# flyte-custom-agent-template
How to write your own custom agent and bring it to a Dockerfile.

## Concepts
1. flytekit will load plugin [here](https://github.com/flyteorg/flytekit/blob/ff2d0da686c82266db4dbf764a009896cf062349/flytekit/__init__.py#L322-L323), 
so you must put your plugin to `entry_points` in [setup.py](https://github.com/Future-Outlier/flyte-custom-agent-template/blob/main/flytekit-bigquery/setup.py).
2. agent registration will be called by loading the plugin, for example, 
bigquery's agent registeration will be called [here](https://github.com/Future-Outlier/flyte-custom-agent/blob/main/flytekit-bigquery/flytekitplugins/bigquery/agent.py#L97)

## Build your own custom agent
1. follow the folder structure in this repo, you can build your own custom agent.
2. build your own custom agent
```bash
docker buildx build --platform linux/amd64 -t localhost:30000/flyteagent:custom-bigquery -f Dockerfile .
```

3. test the image by running it
```bash
docker run -it localhost:30000/flyteagent:custom-bigquery
```

4. check the log (sensor is created by flytekit, bigquery is created by the custom agent)
```
(dev) future@outlier ~ % docker run -it localhost:30000/flyteagent:custom-bigquery
    
WARNING: The requested image's platform (linux/amd64) does not match the detected host platform (linux/arm64/v8) and no specific platform was requested
🚀 Starting the agent service...
Starting up the server to expose the prometheus metrics...
                       Agent Metadata                       
┏━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━┓
┃ Agent Name     ┃ Support Task Types            ┃ Is Sync ┃
┡━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━┩
│ Sensor         │ sensor (v0)                   │ False   │
│ Bigquery Agent │ bigquery_query_job_task (v0)  │ False   │
└────────────────┴───────────────────────────────┴─────────┘
```

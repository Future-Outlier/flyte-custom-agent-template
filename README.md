# flyte-custom-agent
How to write your own custom agent and bring it to a Dockerfile.
1. flytekit will load plugin here
2. agent registration will be caleed by loading the plugin


docker run -it to test if your agent is installed or not
```bash
docker run -it cr.flyte.org/flyteorg/flyteagent:1.13.11
```
the log should be like this
```
(dev) future@outlier ~ % docker run -it cr.flyte.org/flyteorg/flyteagent:1.13.11
🚀 Starting the agent service...
Starting up the server to expose the prometheus metrics...
                             Agent Metadata
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━┓
┃ Agent Name                  ┃ Support Task Types            ┃ Is Sync ┃
┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━┩
│ Sensor                      │ sensor (v0)                   │ False   │
│ Databricks Agent            │ spark (v0) databricks (v0)    │ False   │
│ MMCloud Agent               │ mmcloud_task (v0)             │ False   │
│ Bigquery Agent              │ bigquery_query_job_task (v0)  │ False   │
│ SageMaker Endpoint Agent    │ sagemaker-endpoint (v0)       │ False   │
│ Boto Agent                  │ boto (v0)                     │ True    │
│ Snowflake Agent             │ snowflake (v0)                │ False   │
│ OpenAI Batch Endpoint Agent │ openai-batch (v0)             │ False   │
│ ChatGPT Agent               │ chatgpt (v0)                  │ True    │
│ Airflow Agent               │ airflow (v0)                  │ False   │
└─────────────────────────────┴───────────────────────────────┴─────────┘
```

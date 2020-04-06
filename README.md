# Buildkite On-Demand

Schedule single-shot Buildkite Agents, on-demand, on ECS.

Buildkite on-demand is an event driven Buildkite Agent scheduler. Built on the
Buildkite AWS EventBridge integration, containerised Buildkite Agents are scheduled
using Amazon Elastic Container Service to run on AWS Fargate. An agent is created
for each build and exits immediately on completion. There are no polling agents
so you only pay for the compute time you use.

This repository contains resources and documentation to help you configure an
AWS account to schedule and run agents for your Buildkite Organization in
response to builds.

## Getting Started

First, [deploy the agent-scheduler](agent-scheduler) to an AWS account dedicated
to your continuous integration workload. Then, once agent-scheduler has been
deployed, [deploy task definitions using agent-composer](agent-composer) for the
agents you want to run.

## agent-scheduler

[agent-scheduler](agent-scheduler) is an [AWS SAM](https://aws.amazon.com/serverless/sam/)
project which configures the AWS resources needed to respond to Amazon
EventBridge events from Buildkite and schedule agents on ECS.

## agent-composer

[agent-composer](agent-composer) is a collection of AWS CloudFormation templates
to help create ECS Task Definitions that can be scheduled on-demand by
[agent-scheduler](#agent-scheduler).

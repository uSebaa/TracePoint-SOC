# TracePoint SOC Investigation

A hands on Splunk investigation of unusual authentication activity in a synthetic training dataset.

## Project Overview

This project analyzes authentication events to identify repeated failed logins and check whether a successful login followed from the same source.

## Key Finding

Splunk identified 12 failed login attempts from one source IP targeting four accounts, followed by a successful login to `kguzu` from the same source through `VPN-GATEWAY`.

This is a suspicious pattern in the simulated dataset, not confirmation of a real-world compromise.

## Tools and Skills

- Splunk Enterprise
- Search Processing Language
- Authentication log analysis
- Detection and incident documentation

## Dataset

The project uses 40 synthetic authentication events from the [Splunk SOC Authentication Lab](https://github.com/Khayaguzu/splunk-soc-authentication-lab).

## Case Report

Read the full investigation, assessment, limitations, and recommendations in [the incident report](docs/incident_report.md).

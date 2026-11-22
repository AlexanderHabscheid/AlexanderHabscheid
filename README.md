# Hey, I’m Alexander Habscheid

I build the plumbing that lets AI agents talk to services, move data, and trace what happened. I’m looking for software engineering internships in **backend, infrastructure, and developer tooling**.

## What I’ve shipped

### Orbit · Message bus for AI agents

Orbit gives local agents a NATS-backed way to call services, publish events, and follow a request through retries and timeouts.

[60-second quickstart](https://github.com/AlexanderHabscheid/Orbit#60-second-quickstart) · [RPC implementation](https://github.com/AlexanderHabscheid/Orbit/blob/main/src/rpc_call.ts) · [v0.2.1 release](https://github.com/AlexanderHabscheid/Orbit/releases/tag/v0.2.1)

### Velocity · WebSocket proxy with a latency budget

Velocity adapts its batching window to a p95 latency budget. It ships with a control-plane API and SDKs for TypeScript and Python.

[Quickstart](https://github.com/AlexanderHabscheid/velocity/blob/main/docs/first-15-minutes.md) · [Latency guard](https://github.com/AlexanderHabscheid/velocity/blob/main/src/latency-guard.ts) · [SDKs](https://github.com/AlexanderHabscheid/velocity/tree/main/sdk)

**Velocity benchmark** · Local run of the synthetic `regional` profile

```text
Proxy outbound bytes      99.56% lower vs. unoptimized payload bytes
End-to-end p95 latency     9 ms higher vs. direct WebSocket
```

<details>
<summary>Run the benchmark</summary>

Three repeats, seed 42, Apple Silicon and Node.js 26.5.0. The byte metric uses proxy trace counters. The latency metric compares separate direct and proxied trials. Results depend on workload and environment.

```bash
npx --yes --package=@velocityai/velocity@0.1.3 velocity bench-ci \
  --profiles regional --repeats 3 --seed 42 --fail-on-regression
```

[Benchmark code](https://github.com/AlexanderHabscheid/velocity/blob/main/src/bench-metrics.ts) · [CI benchmark workflow](https://github.com/AlexanderHabscheid/velocity/actions/workflows/velocity-bench.yml)

</details>

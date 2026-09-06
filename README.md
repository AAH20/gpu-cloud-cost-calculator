# GPU Cloud Cost Calculator

An interactive decision tool for comparing managed LLM APIs with self-hosted GPU inference across Azure, AWS, GCP, NVIDIA-based infrastructure, Kubernetes, and vLLM-style serving stacks.

The calculator translates architecture choices into business metrics: monthly cost, cost per successful request, utilization-adjusted GPU cost, availability exposure, and estimated break-even volume.

## Why this exists

GPU purchasing decisions are frequently distorted by comparing API token prices with raw accelerator prices. A production decision also depends on utilization, minimum billed capacity, engineering effort, observability, networking, egress, reliability, and the percentage of requests that actually succeed.

This project makes those assumptions explicit and editable. It is a decision-support model—not a cloud-provider quote or a guarantee of savings.

## Capabilities

- Compare managed API and self-hosted GPU operating models
- Model prompt/output tokens and monthly request volume
- Account for GPU throughput, utilization, replicas, and minimum billed hours
- Include platform engineering, observability, egress, and reliability costs
- Calculate effective cost per successful request
- Estimate the request-volume break-even point
- Generate a live recommendation with the assumptions shown
- Export the current scenario as JSON for review or further analysis
- Responsive UI suitable for architecture workshops and customer discovery

## Decision model

The model evaluates two paths:

1. **Managed API:** token consumption, provider pricing, observability, egress, and expected successful-request rate.
2. **Self-hosted GPU:** accelerator hours, replicas, utilization, minimum capacity, engineering operations, observability, egress, and expected successful-request rate.

All results should be validated against current provider calculators, contractual discounts, regional availability, workload benchmarks, and production SLOs before procurement.

## Technology

- React 19 and TypeScript
- Vinext/Vite application runtime
- Tailwind CSS
- Cloudflare Workers-compatible build output
- GitHub Actions build validation

## Run locally

Requirements: Node.js 22.13 or later.

```bash
npm ci
npm run dev
```

Create a production build:

```bash
npm run build
```

## Evidence and limitations

- Calculations are deterministic from the visible inputs.
- Defaults are illustrative and intentionally editable.
- No result is presented as a vendor quote, benchmark, or financial guarantee.
- Hardware availability, reserved-capacity discounts, tax, data residency, and workload-specific latency must be evaluated separately.

## Commercial architecture support

Need a workload-specific Azure, multi-cloud, AI infrastructure, networking, security, or FinOps assessment? Visit [A2Z SOC](https://a2zsoc.com/).

## License

Copyright (c) Ahmed Hassan. All rights reserved unless a separate license is added.

# FactorGuide

**Decision intelligence for AI agents.** Send a coupling matrix — get zone classifications, optimal factorization strategy, and calibrated risk predictions.

Every system with interacting variables has a coupling structure. When an agent simplifies that system by treating variables as independent, it pays an information cost. FactorGuide quantifies that cost exactly.

## Quick Start

### MCP (Model Context Protocol)

FactorGuide is listed on the [Official MCP Registry](https://registry.modelcontextprotocol.io/). Any MCP-compatible agent discovers tools automatically:

```
mcp_endpoint: https://factorguide.io/mcp
```

### HTTP REST

```
POST https://factorguide.io/navigate
POST https://factorguide.io/diagnose
POST https://factorguide.io/explain
POST https://factorguide.io/report_outcome
```

### Agent Discovery

```
GET https://factorguide.io/llms.txt
GET https://factorguide.io/openapi.json
```

## Example

Send a 3×3 correlation matrix:

```json
{
  "coupling": {
    "covariance_matrix": [
      [1.00, 0.72, 0.05],
      [0.72, 1.00, 0.48],
      [0.05, 0.48, 1.00]
    ]
  },
  "sample_size": 500,
  "model_class": "constitutive"
}
```

Get back zone classifications:

| Pair | IC | Zone | Recommendation |
|------|-----|------|----------------|
| z0–z1 | 0.682 | 3 | **PRESERVE** |
| z0–z2 | 0.031 | 1 | FACTORIZE |
| z1–z2 | 0.453 | 2 | ASSESS |

- **Zone 1**: Safe to factorize. Coupling below threshold.
- **Zone 2**: Depends on functional role. Same IC, opposite recommendations for constitutive vs. inductive coupling.
- **Zone 3**: Must preserve. Coupling is load-bearing regardless of model class.

## Pricing

| Tier | Price | Queries | Max Variables |
|------|-------|---------|---------------|
| Trial | Free | 15 per wallet | n ≤ 25 |
| Starter | $0.05/query | 50–200 bundles | n ≤ 100 |
| Professional | $0.03/query | 500–2000 bundles | n ≤ 1000 |

Payment: USDC on Base via x402 or MPP. `report_outcome` is always free.

## Data Privacy

FactorGuide accepts only second-order summary statistics — covariance, precision, correlation matrices, or edge lists. No raw observations. Matrices are zeroed after IC computation.

## Theoretical Foundation

Built on [Circulatory Fidelity](https://circulatoryfidelity.com), a mathematical framework where IC (Inference Coupling) measures the partial correlation between variables. The cost function V(IC) gives the exact mutual information destroyed by severing a coupling. Risk curves are calibrated on 49,000+ validated datapoints.

Every prediction is falsifiable. When agents report outcomes, the flywheel refines future predictions.

## Links

- **Website**: [factorguide.io](https://factorguide.io)
- **Theory**: [circulatoryfidelity.com](https://circulatoryfidelity.com)
- **MCP Registry**: [registry.modelcontextprotocol.io](https://registry.modelcontextprotocol.io/)

---

Built by [CF Laboratory](https://circulatoryfidelity.com)

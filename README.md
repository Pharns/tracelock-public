# TraceLock - Multi-Domain RF Threat Detection (Public Overview)

![Status](https://img.shields.io/badge/status-public--safe-brightgreen)
![Scope](https://img.shields.io/badge/scope-redacted-blue)
![License](https://img.shields.io/badge/license-proprietary-lightgrey)
![CI/CD](https://img.shields.io/badge/ci%2Fcd-implemented-informational)

TraceLock is a defensive, passive RF telemetry platform for multi-domain wireless awareness. This public repository is a redacted overview that demonstrates detection engineering and evidence-grade logging without exposing sensitive methods or operational details.

## What This Is
- Passive signal observation across Wi-Fi, BLE, SDR, GPS, and ADS-B
- Evidence-grade logging with integrity checks and structured outputs
- Detection engineering focused on correlation, not active interference

## Domains Covered (Defensive)
- Wi-Fi (beacons, probe patterns, rogue AP indicators)
- BLE (advertisement density, device class patterns)
- SDR (wideband spectrum context)
- GPS (signal quality anomalies)
- ADS-B (aircraft proximity context)

## High-Level Architecture (Redacted)

```mermaid
flowchart LR
  Sensors[Passive Sensors] --> Normalizer[Signal Normalizer]
  Normalizer --> Correlator[Multi-Domain Correlation]
  Correlator --> Evidence[(Evidence Store)]
  Correlator --> Detections[Detection Rules]
  Detections --> Reports[Reports + Exports]
```

## Evidence Pipeline (Redacted)

```mermaid
sequenceDiagram
  participant Capture
  participant Normalize
  participant Store
  participant Report
  Capture->>Normalize: Raw observations
  Normalize->>Store: Structured logs + hashes
  Store-->>Report: Summary + findings
```

## Detection Categories (High-Level)
- **Baseline drift**: density spikes, time-of-day anomalies, out-of-pattern device classes
- **Rogue infrastructure**: beacon mismatches, duplicate identifiers, unexpected SSID profiles
- **Signal health**: RF noise shifts, spectrum saturation events, GPS quality anomalies
- **Proximity context**: ADS-B activity correlated to local RF changes

## Evidence Schema (Redacted)
Fields used in structured logs (values are redacted or synthetic in public artifacts):

| Field | Type | Purpose |
| --- | --- | --- |
| `scan_id` | string | Unique run identifier |
| `window_utc` | string | Capture time range |
| `domain` | string | wifi, ble, sdr, gps, adsb |
| `observation_count` | number | Volume summary |
| `alert_count` | number | Detection count |
| `summary` | string | Human-readable finding |
| `severity` | string | low, medium, high |
| `action` | string | Recommended next step |
| `integrity` | object | Hashes + manifest pointer |

## Governance Workflow (Defensive)
1. Capture passive observations within authorized scope.
2. Normalize and log with integrity metadata.
3. Correlate signals across domains to reduce false positives.
4. Produce a short, decision-ready report with recommended actions.
5. Update baselines and document outcomes for auditability.

## Example Outputs (Synthetic)
- `examples/trace-lock-scan-summary.json`
- `examples/detection-report.md`

## CI/CD (Private Repo)
This public overview mirrors a private repo with automated workflows:
- CI: lint + smoke tests for core modules
- Gates: compile checks and basic entrypoint validation
- Hygiene: dependency install and runtime guards

## Safety and Scope
- Defensive-only, passive observation
- No jamming, no interference, no device targeting
- No real device identifiers or addresses in public artifacts

## Redaction Policy
- No MACs, SSIDs, GPS coordinates, or device IDs.
- No operational timelines tied to real locations.
- No implementation details that enable active interference.

## Disclaimer
This is a public-safe overview. Do not use as a production system. No sensitive data or operational details are included.

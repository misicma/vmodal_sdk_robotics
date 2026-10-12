# VModal Robotics SDK v0.2.0 – Community Testing Report

*Tested on: Ubuntu 22.04 | Python 3.10 | LeRobot v3*

---

## Installation

```bash
pip install vmodal-sdk
```

> ⚠️ **Known pip bug:** The package installs as `UNKNOWN 0.0.0` instead of `vmodal-sdk 0.2.0`.
> This is caused by dynamic versioning in `pyproject.toml`. The package still works correctly.

```bash
$ pip show vmodal-sdk
Name: UNKNOWN
Version: 0.0.0
```

**Workaround:** Clone the repository and install from source:

```bash
git clone https://github.com/v-modal/vmodal_sdk_robotics
cd vmodal_sdk_robotics
pip install -e .
```

Verify installation:

```bash
$ python3 -m vmodal --help
```

> ⚠️ **Note:** Use `python3` instead of `python` on Ubuntu/Debian systems.

---

## Running the Tests

```bash
bash test.sh
```

### Test Results – All 12 Suites Passed ✅

| Test Suite | Status |
|---|---|
| SDK Import | ✅ PASSED |
| Configuration Loading | ✅ PASSED |
| Robot Connection | ✅ PASSED |
| Sensor Data | ✅ PASSED |
| Motion Planning | ✅ PASSED |
| LeRobot v3 Integration | ✅ PASSED |
| Cloud Upload | ✅ PASSED |
| Data Serialization | ✅ PASSED |
| Error Handling | ✅ PASSED |
| Authentication | ✅ PASSED |
| Telemetry | ✅ PASSED |
| End-to-End Pipeline | ✅ PASSED |

> Tests run on synthetic/simulated data (no physical robot required).

---

## Transport Qualification Status

```json
{
  "transport_qualification": {
    "qualified": false,
    "missing_capabilities": 9
  }
}
```

The SDK is **not yet transport-qualified** – 9 capabilities are still missing for full qualification. This is expected for v0.2.0 (early development stage).

---

## Known Issues

| # | Issue | Severity |
|---|---|---|
| 1 | `pip install` shows `UNKNOWN 0.0.0` instead of correct package name/version | Medium |
| 2 | `python` command fails on Ubuntu/Debian – must use `python3` | Low |
| 3 | `transport_qualification: qualified=false` – 9 missing capabilities | Expected |

---

## Development Roadmap (from `docs/todo/fixes_v1.md`)

**P0 – Critical fixes:**
- Fix dynamic versioning in `pyproject.toml` so pip shows correct package metadata
- Fix `python` vs `python3` invocation issue

**P1 – Next milestone:**
- Implement the 9 missing transport capabilities to achieve `qualified=true`
- Replace synthetic test data with real hardware validation

---

## Summary

VModal SDK v0.2.0 is functional for development and testing purposes. All 12 test suites pass on synthetic data. The two installation bugs (pip metadata, python3 invocation) are minor and have simple workarounds. The SDK is on track for v1.0 qualification once the missing transport capabilities are implemented.

**Repo:** https://github.com/v-modal/vmodal_sdk_robotics/tree/main/lerobot

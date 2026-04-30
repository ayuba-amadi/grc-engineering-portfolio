# Methodology

This section explains how the lab was designed and executed.

## Approach

The lab follows a structured GRC-driven methodology:

1. Identify risk
2. Define control
3. Implement control
4. Simulate risk events
5. Monitor detection
6. Validate effectiveness
7. Map to compliance frameworks

---

## Risk Definition

Unauthorized modification of sensitive financial files.

---

## Control Selection

File Integrity Monitoring (FIM) was selected as a detective control.

---

## Execution Steps

1. Configure monitored directory
2. Perform file operations
3. Collect alerts from Wazuh
4. Analyze event details
5. Map alerts to compliance frameworks

---

## Validation Criteria

The control is considered effective if:

- All file events are detected
- Alerts contain full details
- Evidence is centrally logged

---

## Outcome

The control successfully met all validation criteria.

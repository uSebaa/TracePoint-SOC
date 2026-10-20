# TracePoint SOC Investigation

## Case Summary

This case study uses Splunk to investigate unusual authentication activity in a synthetic training dataset. The analysis focused on repeated failed logins and whether they were followed by a successful login from the same source.

## Dataset and Scope

- **Dataset:** `splunk_authentication_logs.csv`
- **Events analyzed:** 40
- **Platform:** Splunk Enterprise
- **Scope:** Login successes, login failures, and logouts

The dataset is synthetic and intended for training.

## Investigation Findings

Splunk identified 12 failed login attempts from `203.0.113.50` between `09:02:11` and `09:04:35` on `2026-08-07`. The attempts targeted four accounts: `admin`, `administrator`, `kguzu`, and `root`.

At `09:04:49`, account `kguzu` successfully logged in from the same IP through `VPN-GATEWAY`, 14 seconds after the final failed attempt. Other recorded successful activity for `kguzu` used `192.168.10.15` and `WORKSTATION-01`.

The detection search returned this one successful login after at least five failed attempts from the same IP.

## Assessment

This sequence is suspicious and consistent with a possible account compromise in the simulated scenario. The authentication data alone does not confirm that the login was unauthorized or that a real account was compromised.

## Recommendations

1. Confirm whether the `kguzu` VPN login was authorized.
2. Review VPN, identity, and MFA records around the event time.
3. If unauthorized, secure the account, revoke active sessions, and reset its credentials.
4. Preserve relevant logs for follow-up investigation.

## Limitations

- The dataset contains only 40 synthetic events covering a limited period.
- MFA, endpoint, and session activity are not available, so the data cannot establish a reliable long-term user baseline or confirm compromise.
- The source IP `203.0.113.50` is used for documentation and training purposes and does not identify a real attacker.

## Conclusion

This investigation demonstrates how Splunk can summarize authentication events and identify a successful login following repeated failures. The result is a training-lab finding that requires validation, not proof of a real-world attack.

# BrightLeaf Organics - Security Assessment & Incident Report

This repository contains my final cybersecurity capstone report, presentation slides, and lab evidence for BrightLeaf Organics, combining network reconnaissance, SSH log monitoring, incident response, disk forensics, GRC risk scoring, and cloud IAM auditing.

## Repository Contents
- `report/brightleaf_security_assessment_report.pdf` - Written Security Assessment Report
- `slides/brightleaf_capstone_presentation.pdf` - 9-slide Capstone Presentation Deck
- `evidence/day15_auth.log` - SSH authentication log from server websrv01
- `evidence/day19_cloud_config.json` - Cloud IAM and storage configuration file
- `README.md` - Overview of findings and remediation priorities

## Key Findings
1. **SSH Brute-Force & Backdoor Account (websrv01):** External IP `203.0.113.77` ran 60 failed SSH login attempts against `admin` before authenticating at `02:16:13` and creating rogue account `svc_update` via `sudo`.
2. **Data Staging & Exfiltration (Disk Forensics):** SHA-256 verification and Autopsy analysis of `day17_evidence.img` recovered deleted file `SECRET.TXT`, confirming compromised account `m.shah` staged data at `02:40` and uploaded it to `203.0.113.77`.
3. **Cloud IAM & Storage Misconfigurations:** Audit of `day19_cloud_config.json` found public unencrypted customer records (`brightleaf-customer-data`), an active admin access key on public GitHub (`AKIA_EXAMPLE_LIVEKEY_1234`), wildcard IAM roles without MFA, and ports 22 and 3306 open to `0.0.0.0/0`.
4. **Risk Register & IR Playbook:** Scored 7 operational risks on a 5x5 matrix and documented a 6-step NIST Incident Response playbook.

# VMWare-Ansible – Repository Structure & Workflow Guide

This document explains the folder structure of the repo and how you should work with branches, commits, and Pull Requests (PRs).

---

## 1. Repository Structure

```text
vmware-ansible/
├── docs/
│   └── session1.md                    # Session 1 lab guide
│   └── repo-structure-and-workflow.md # This document
├── inventory.yml                      # Ansible inventory (vCenter group)
├── group_vars/
│   ├── vcenter.yml.example            # Template for vCenter vars (safe to commit)
│   └── vcenter.yml                    # REAL vCenter credentials (ignored by Git)
├── playbooks/
│   └── vcenter_about.yml              # Test playbook to get vCenter info
├── .github/
│   ├── pull_request_template.md       # PR template
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md              # Bug report issue template
│   │   └── feature_request.md         # Feature request issue template
│   └── workflows/
│       └── ci.yml                     # GitHub Actions workflow (basic checks)
├── .gitignore                         # Ignore secrets, logs, etc.
├── README.md                          # High-level overview of the project

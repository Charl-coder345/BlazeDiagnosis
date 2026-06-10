# Day 2 Task 4 - Github Security Hygiene Checklist

# GitHub Security Hygiene Checklist

## Repository Configuration

- [ ] Repository visibility (public/private) is appropriate
- [ ] Unused repositories have been archived or deleted
- [ ] Repository descriptions do not expose sensitive information
- [ ] Branch protection rules are enabled
- [ ] Force pushes to protected branches are disabled
- [ ] Pull requests are required before merging to the main branch
- [ ] Required code reviews are enabled
- [ ] Commit signing is enforced where appropriate

## User Access and Permissions

- [ ] Access follows the principle of least privilege
- [ ] Only authorized users have repository access
- [ ] Former employees and contractors have been removed
- [ ] Administrative privileges are restricted
- [ ] Team permissions are reviewed regularly
- [ ] Two-factor authentication (2FA) is enabled for all users
- [ ] Personal Access Tokens (PATs) are reviewed periodically

## Passwords and Secrets

- [ ] No passwords are hardcoded in source code
- [ ] No API keys are stored in repositories
- [ ] Environment variables are used for secrets
- [ ] .env files are excluded through .gitignore
- [ ] SSH keys are stored securely
- [ ] Credentials are rotated regularly
- [ ] Compromised credentials can be revoked quickly
- [ ] Secret management solutions are used where appropriate

## GitHub Secret Exposure Prevention

- [ ] GitHub Secret Scanning is enabled
- [ ] Push Protection is enabled
- [ ] Repository history has been checked for exposed secrets
- [ ] GitHub Actions use ${{ secrets.NAME }}
- [ ] Workflow files do not contain hardcoded credentials
- [ ] Logs do not reveal secrets or tokens
- [ ] Backup files containing credentials are excluded from source control

## Code Quality and Secure Development

- [ ] Pull requests are reviewed before merging
- [ ] Secure coding guidelines are followed
- [ ] Input validation is implemented
- [ ] Error messages do not reveal sensitive information
- [ ] Dependencies are reviewed before use
- [ ] Static code analysis tools are used
- [ ] Security testing is included in the development process

## Dependency and Vulnerability Management

- [ ] Dependabot alerts are enabled
- [ ] Dependabot security updates are enabled
- [ ] Third-party libraries are regularly updated
- [ ] Unsupported software versions have been removed
- [ ] Known vulnerabilities are remediated promptly
- [ ] Software dependencies are documented
- [ ] License compliance is reviewed

## GitHub Actions and CI/CD Security

- [ ] GitHub Actions permissions are minimized
- [ ] Workflows use GitHub Secrets instead of hardcoded credentials
- [ ] Third-party actions are trusted and reviewed
- [ ] Workflow logs do not expose sensitive information
- [ ] Production deployments require approval
- [ ] Self-hosted runners are secured and monitored
- [ ] CI/CD pipelines are tested regularly

## Monitoring and Logging

- [ ] Audit logs are reviewed regularly
- [ ] Security alerts are monitored
- [ ] Failed login attempts are investigated
- [ ] Suspicious activity is reported promptly
- [ ] Logging mechanisms are enabled
- [ ] Incident response procedures are documented

## Backup and Recovery

- [ ] Repository backups are performed regularly
- [ ] Backup files are protected
- [ ] Recovery procedures are documented
- [ ] Disaster recovery plans are tested periodically
- [ ] Critical repositories have redundancy measures in place

## Compliance and Governance

- [ ] Security policies are documented
- [ ] Repository ownership is clearly defined
- [ ] Developers receive security awareness training
- [ ] Security reviews are performed periodically
- [ ] Compliance requirements are identified
- [ ] Incident response procedures are available
- [ ] Security responsibilities are assigned

## Overall Security Rating

```markdown
Score	        Security Posture
90–100%	        Excellent
75–89%	        Good
60–74%	        Fair
Below 60%	    Improvement Requireds
```
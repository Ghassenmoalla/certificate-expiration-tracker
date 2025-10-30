# Certificate Expiration Tracker

## Overview  
Developed an Ansible playbook to monitor SSL certificate expiry across Windows servers:  
- Scans the “Personal” certificate store on target hosts  
- Identifies expired certificates and those expiring within 14 days  
- Outputs results in JSON / human-readable format  
- Designed to be integrated into monitoring or CI/CD pipelines

## Tech Stack  
- Ansible (YAML)  
- Windows target hosts (WinRM / PSRP)  
- `ansible.windows.win_certificate_info` module :contentReference[oaicite:0]{index=0}  
- Jinja2 filters & timestamp calculations  
- (Optional) JSON export for further processing

## Key Highlights  
- Automated collection of certificate metadata (issued_to, valid_to_iso8601, thumbprint)  
- Logic to compute `days_left` for soon-to-expire certificates  
- Conditional tasks using `when` and `loop_control` for clear debug output  
- Modular design with reusable variable `variable_host` for host targeting  
- Export/reporting capability for audit/compliance workflows  

## What I Learned / Value Added  
- Deepened experience with Windows automation via Ansible  
- Developed timestamp and date-based logic using Jinja2 filters and `now()`  
- Improved skills in configuration management, automation and observability in enterprise environments  
- Enhanced my portfolio as a DevOps/cloud engineer demonstrating real-world Windows/automation use case  

## Usage  
```bash
ansible-playbook playbooks/cert_expiration_tracker.yml -e "variable_host=iis_server"

Project Setup Guide
📂 Clone the Repository

Clone all project files into the same directory:

git clone <repository-url>
cd <repository-folder>

🔐 SSL Certificate Setup

    Create a directory for certificates:

mkdir certs

    Configure a Let's Encrypt renewal hook to copy the updated certificates into the certs directory and set the correct owner:

Create a script in /etc/letsencrypt/renewal-hooks/deploy/:

#!/bin/bash
cp /etc/letsencrypt/live/<your-domain>/* /path/to/your/project/certs/
chown -R <grafana-docker-user>:<grafana-docker-user-group> /path/to/your/project/certs/

Make it executable:

chmod +x /etc/letsencrypt/renewal-hooks/deploy/<script-name>.sh

✅ This ensures certificates are renewed and available for Grafana.
📊 Import Dashboards into Grafana

    Open your Grafana UI.

    Go to:
    Dashboards → Import → Upload JSON file

    Select the provided .json dashboard files from this repository.

✅ Summary

    Clone all files into the same directory.

    Create a certs directory and configure the renewal hook for certificates.

    Change ownership to the Grafana Docker user.

    Import JSON dashboards into Grafana via the UI.

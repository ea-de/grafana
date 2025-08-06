Project Setup Guide
📂 Clone the Repository

Clone all project files into the same directory:

    git clone git@github.com:ea-de/grafana.git

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

Open your Grafana UI & then Dashboards → Import → Upload JSON file. Select the provided .json dashboard files from this repository.

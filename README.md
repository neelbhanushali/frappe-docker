# Steps
- docker compose -p frappe-docker --env-file .\compose.env.example -f .\dependencies.yml up -d
- docker compose -p frappe-docker --env-file .\compose.env.example -f .\nginx.yml up -d
- docker compose -p frappe-docker --env-file .\compose.env.example -f .\frappe.yml up -d
- docker compose -p frappe-docker --env-file .\compose.env.example -f .\site.yml up -d

# Steps
- git clone https://github.com/neelbhanushali/frappe-docker.git && cd frappe-docker
- docker network create frappe_network
- cp compose.env.example compose.env
- docker compose -p frappe-docker --env-file compose.env -f dependencies.yml up -d
- docker compose -p frappe-docker --env-file compose.env -f nginx.yml up -d
- docker compose -p frappe-docker --env-file compose.env -f frappe.yml up -d
- docker exec backend bench get-app crm
- docker exec backend ln -s /home/frappe/frappe-bench/apps/crm/crm/public /home/frappe/frappe-bench/sites/assets/crm
- docker exec backend ln -s /home/frappe/frappe-bench/apps/frappe/frappe/public /home/frappe/frappe-bench/sites/assets/frappe
- docker exec backend ln -s /home/frappe/frappe-bench/apps/erpnext/erpnext/public /home/frappe/frappe-bench/sites/assets/erpnext
- docker exec backend bench new-site --no-mariadb-socket --admin-password=admin --install-app erpnext --set-default abcd
- docker compose -p frappe-docker --env-file compose.env -f site.yml up -d

# transport-management-system

## Architecture folder

 - apps: for develepment odoo website, module. See more for dev: [documentation](https://www.odoo.com/documentation/12.0/index.html)
 - config: main config file, requirements, ...
 - data-files(only save to your local): logs, odoo filestore, db dump, ...
 - modules: contain dependencies for the module
 - odoo: repository of main framework at [odoo](https://github.com/thangquoctranqb/odoo.git)
 - python-env(only save to your local): virtualenv project

## Setup Guideline

### 1. Install the requirement
*** Note: [python3](https://www.python.org/downloads), [nodejs](https://nodejs.org/en/download) is required

- Install rtlcss: `npm install -g rtlcss`
- Download & install wkhtmltopdf at [https://wkhtmltopdf.org/downloads.html](https://wkhtmltopdf.org/downloads.html)
- Install python modules: `pip3 install -r config/requirements-py.txt`

Clone repositories:

- project: `git clone --depth 1 --branch 12.0 --single-branch https://github.com/thangquoctranqb/transport-management-system.git`
- odoo: `cd transport-management-system && git clone --depth 1 --branch 12.0 --single-branch https://github.com/thangquoctranqb/odoo.git` 

### 2. Configuration
See detail at "config/odoo.conf"
Todo ...

### 3. Import database
*** Note: [postgres 10](https://www.postgresql.org/download) is required

- Create role & user:
`psql && \du`
`CREATE USER tms WITH SUPERUSER LOGIN PASSWORD 'tms';`

- Restore database:
`psql`
`CREATE DATABASE tms;`
`psql --set ON_ERROR_STOP=on -U tms -d tms < data-files/dump/tmsdb-dump*;`

See detail at "data-files/tmsdb-dump*"

### 4. Run system
Start: `./odoo-bin -c config/odoo.conf`

Access at localhost: [http://127.0.0.1:8069](http://127.0.0.1:8069)

User login: admin@gmail.com/admin

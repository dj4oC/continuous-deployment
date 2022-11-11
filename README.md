# Continuous Deployment

## Usage

This continuous deployment playbook assumes:
- you are using Hetzner Cloud for your servers
- you are using Cloudflare for your DNS records
- your deployments are defined with docker-compose

### Install requirements
1. run `pip --version` to test whether pip is installed. Since pip is usally linked to python2 you might need to redirect it to python3. You can test this running `pip3 --version`. If this test is successfull, you can easly link pip3 to pip by adding an alias. To do so run `alias pip=pip3`
1. run `pip install -r py-requirements.txt`
1. run `ansible-galaxy role install -r requirements.yml --force`
1. run `ansible-galaxy collection install -r requirements.yml --force`

### run all (create hcloud server, add cloudflare DNS record, configure ubuntu, deploy docker-compose project)

1. add your server and docker-compose projects to `servers.yml`
1. run `export HCLOUD_API_TOKEN=...` with a valid Hetzner cloud api token
1. run `export CLOUDFLARE_API_TOKEN=...` with a valid Cloudflare api token
1. run `ansible-playbook playbook-all.yml`

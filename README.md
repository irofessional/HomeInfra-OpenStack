# HomeInfra-OpenStack

## How To Use

### Install dependency

```
sudo apt install python3-venv python3-dev libffi-dev gcc libssl-dev git
```

### Get source
clone at home directory

```
cd ~
git clone https://github.com/irofessional/HomeInfra-OpenStack.git
```

### Setup venv

```
cd HomeInfra-OpenStack
python3 -m venv .env
source .env/bin/activate
```

### Install Kolla-Ansible

```
pip install -U pip
pip install 'ansible<5.0'
pip install git+https://opendev.org/openstack/kolla-ansible@master
```

### Deploy

```
export KOLLA_BASE_DIR=$HOME/HomeInfra-OpenStack
kolla-ansible -i inventory/all-in-one --configdir $KOLLA_BASE_DIR --passwords $KOLLA_BASE_DIR/passwords.yml --ask-vault-pass bootstrap-servers
kolla-ansible -i inventory/all-in-one --configdir $KOLLA_BASE_DIR --passwords $KOLLA_BASE_DIR/passwords.yml --ask-vault-pass prechecks
kolla-ansible -i inventory/all-in-one --configdir $KOLLA_BASE_DIR --passwords $KOLLA_BASE_DIR/passwords.yml --ask-vault-pass deploy
```